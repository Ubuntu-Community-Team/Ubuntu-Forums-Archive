---
title: "Samba not starting at boot after 9.10 upgrade"
date: 2010-03-14
forum: Server Platforms
---

### Post by ris8 on 2010-03-14
I have a file server running samba 3.4.0. I just upgraded ubuntu to 9.10. The upgrade was unfortunately stopped in the middle, but I think I managed to complete it.
The problem is that now samba will not work after a reboot. The daemons are running, but any attempt to connect from a windows machine fails (Windows 7: the network path was not found). Manually restarting the service fixes the problem, but I need a more stable solution!
Interestingly, I can ssh to the machine, or rdp to a virtual machine running on it.

The logs don't seem to report any error:

```
stefano@SERVER02:/var/log/samba$ tail log.smbd
[2010/03/14 04:02:11,  0] smbd/server.c:1068(main)
  smbd version 3.4.0 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/03/14 04:02:15,  1] smbd/process.c:755 smbd_sig_hup_handler)
  Reloading services after SIGHUP

stefano@SERVER02:/var/log/samba$ tail log.nmbd
[2010/03/14 04:02:11,  0] nmbd/nmbd_subnetdb.c:206(create_subnets)
  create_subnets: No local IPv4 non-loopback interfaces !
[2010/03/14 04:02:11,  0] nmbd/nmbd_subnetdb.c:207(create_subnets)
  create_subnets: Waiting for an interface to appear ...
[2010/03/14 04:02:40,  0] nmbd/nmbd_become_lmb.c:395(become_local_master_stage2)
  *****

  Samba name server SERVER02 is now a local master browser for workgroup CUGIARISA on subnet 192.168.100.200

  *****
```

This is my smb.conf:
```
[global]
workgroup = ####
netbios name = SERVER02
nt acl support = yes
inherit permissions = yes
inherit acls = yes
map acl inherit = yes
acl compatibility = auto
dos filemode = yes
dos filetimes = yes
dos filetime resolution = yes
null passwords = yes

server string = %h server (Samba, Ubuntu)
interfaces = 127.0.0.0/8 br0
bind interfaces only = yes
panic action = /usr/share/samba/panic-action %d
winbind enum groups = yes
winbind enum users = yes
socket options = TCP_NODELAY SO_RCVBUF=131072 SO_SNDBUF=131072 IPTOS_LOWDELAY SO_KEEPALIVE 
load printers = no
dead time = 15
getwd cache = yes


[####]
comment = #####
path = /export/share01/#####
read only = No
writeable = yes
create mask = 0700
directory mask = 0700
acl group control = yes
store dos attributes = yes

<more...>
```

---

### Post by ris8 on 2010-03-14
A little more info as I keep trying...

The console shows a reloading samba, smb.conf only and a restarting ssh. It shows these messages right *after* it asks for a login. A little web search this may be related to dhcp acquiring a new ip. Not sure this is even an issue as I never use the console so I don't know if it's normal.

Anyhow, I should have mentioned I can ping the windows machines from the server and viceversa.

If I try to access the service from the server itself I get a connection refused... even after restarting it (note that after restart I can access it from Windows):

```
stefano@SERVER02:/etc$ smbclient -L server02
Enter stefano's password:
Connection to server02 failed (Error NT_STATUS_CONNECTION_REFUSED)
stefano@SERVER02:/etc$ ps -AF | grep mbd
root      2105     1  0 14574  1920   0 13:40 ?        00:00:00 /usr/sbin/nmbd -
D
root      2108     1  0 23531  3308   1 13:40 ?        00:00:00 /usr/sbin/smbd -
D
root      2212  2108  0 23531  2108   1 13:40 ?        00:00:00 /usr/sbin/smbd -
D
stefano   2625  2450  0  1832   876   1 14:14 pts/1    00:00:00 grep mbd
stefano@SERVER02:/etc$ sudo /etc/init.d/samba status
[sudo] password for stefano:
 * nmbd is running
 * smbd is running
stefano@SERVER02:/etc$ smbclient -L server02
Enter stefano's password:
Connection to server02 failed (Error NT_STATUS_CONNECTION_REFUSED)
stefano@SERVER02:/etc$ sudo /etc/init.d/samba restart
 * Stopping Samba daemons                                                [ OK ]
 * Starting Samba daemons                                                [ OK ]
stefano@SERVER02:/etc$ smbclient -L server02
Enter stefano's password:
Connection to server02 failed (Error NT_STATUS_CONNECTION_REFUSED)
```

---

### Post by ris8 on 2010-03-14
I also see the requests from the windows machines in the log.nmbd:

```
[2010/03/14 14:49:36,  3] nmbd/nmbd_incomingrequests.c:453(process_name_query_request)
  process_name_query_request: Name query from 192.168.100.100 on subnet 192.168.100.200 for name ISATAP<00>
[2010/03/14 14:49:36,  3] nmbd/nmbd_incomingrequests.c:453(process_name_query_request)
  process_name_query_request: Name query from 192.168.100.100 on subnet 192.168.100.200 for name ISATAP<00>
```

It all seems to point to an improperly started smbd, but the smbd is running... looking at debug level 3 log.smbd I only see a "Failed to fetch domain sid for CUGIARISA" (is this a problem?):

```
[2010/03/14 14:33:35,  3] smbd/server.c:848(exit_server_common)
  Server exit (termination signal)
[2010/03/14 14:34:57,  0] smbd/server.c:1068(main)
  smbd version 3.4.0 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/03/14 14:34:57,  2] lib/tallocmsg.c:106(register_msg_pool_usage)
  Registered MSG_REQ_POOL_USAGE
[2010/03/14 14:34:57,  2] lib/dmallocmsg.c:77(register_dmalloc_msgs)
  Registered MSG_REQ_DMALLOC_MARK and LOG_CHANGED
[2010/03/14 14:34:57,  3] param/loadparm.c:9016(lp_load_ex)
  lp_load_ex: refreshing parameters
Initialising global parameters
[2010/03/14 14:34:57,  3] ../lib/util/params.c:550(pm_process)
  params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
[2010/03/14 14:34:57,  3] param/loadparm.c:7703(do_section)
  Processing section "[global]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[stefano]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[carla]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[marcello]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[HTPC]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[public]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[DVD]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[private]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[Fantom]"
[2010/03/14 14:34:57,  3] param/loadparm.c:6174(lp_add_ipc)
  adding IPC service
[2010/03/14 14:34:57,  2] lib/interface.c:463(interpret_interface)
  interpret_interface: using netmask value 8 from config file on interface lo
[2010/03/14 14:34:57,  2] lib/interface.c:340(add_interface)
  added interface lo ip=127.0.0.1 bcast=127.255.255.255 netmask=255.0.0.0
[2010/03/14 14:34:57,  2] lib/interface.c:340(add_interface)
  added interface br0 ip=fe80::215:17ff:fec7:b3e5%br0 bcast=fe80::ffff:ffff:ffff:ffff%br0 netmask=ffff:ffff:ffff:ffff::
[2010/03/14 14:34:57,  3] smbd/server.c:1110(main)
  loaded services
[2010/03/14 14:34:57,  3] smbd/server.c:1125(main)
  Becoming a daemon.
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2010/03/14 14:34:57,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] auth/token_util.c:433(create_local_nt_token)
  Failed to fetch domain sid for CUGIARISA
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] auth/token_util.c:464(create_local_nt_token)
  Failed to fetch domain sid for CUGIARISA
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] lib/privileges.c:63(get_privileges)
  get_privileges: No privileges assigned to SID [S-1-22-1-0]
[2010/03/14 14:34:57,  3] lib/privileges.c:63(get_privileges)
  get_privileges: No privileges assigned to SID [S-1-5-2]
[2010/03/14 14:34:57,  3] lib/privileges.c:63(get_privileges)
  get_privileges: No privileges assigned to SID [S-1-5-11]
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] auth/token_util.c:433(create_local_nt_token)
  Failed to fetch domain sid for CUGIARISA
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] auth/token_util.c:464(create_local_nt_token)
  Failed to fetch domain sid for CUGIARISA
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] lib/privileges.c:63(get_privileges)
  get_privileges: No privileges assigned to SID [S-1-5-21-2063038000-3907146246-2208747359-501]
[2010/03/14 14:34:57,  3] lib/privileges.c:63(get_privileges)
  get_privileges: No privileges assigned to SID [S-1-22-2-65534]
[2010/03/14 14:34:57,  3] lib/privileges.c:63(get_privileges)
  get_privileges: No privileges assigned to SID [S-1-5-2]
[2010/03/14 14:34:57,  3] lib/privileges.c:63(get_privileges)
  get_privileges: No privileges assigned to SID [S-1-5-32-546]
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] printing/printing.c:1415(start_background_queue)
  start_background_queue: Starting background LPQ thread
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  1] smbd/process.c:755(smbd_sig_hup_handler)
  Reloading services after SIGHUP
[2010/03/14 14:34:57,  3] param/loadparm.c:9016(lp_load_ex)
  lp_load_ex: refreshing parameters
Initialising global parameters
[2010/03/14 14:34:57,  3] ../lib/util/params.c:550(pm_process)
  params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
[2010/03/14 14:34:57,  3] param/loadparm.c:7703(do_section)
  Processing section "[global]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[stefano]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[carla]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[marcello]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[HTPC]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[public]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[DVD]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[private]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[Fantom]"
[2010/03/14 14:34:57,  3] param/loadparm.c:6174(lp_add_ipc)
  adding IPC service
[2010/03/14 14:34:57,  2] lib/interface.c:463(interpret_interface)
  interpret_interface: using netmask value 8 from config file on interface lo
[2010/03/14 14:34:57,  2] lib/interface.c:340(add_interface)
  added interface lo ip=127.0.0.1 bcast=127.255.255.255 netmask=255.0.0.0
[2010/03/14 14:34:57,  2] lib/interface.c:340(add_interface)
  added interface br0 ip=fe80::215:17ff:fec7:b3e5%br0 bcast=fe80::ffff:ffff:ffff:ffff%br0 netmask=ffff:ffff:ffff:ffff::
[2010/03/14 14:34:57,  2] lib/interface.c:340(add_interface)
  added interface br0 ip=192.168.100.200 bcast=192.168.100.255 netmask=255.255.255.0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  1] smbd/process.c:755(smbd_sig_hup_handler)
  Reloading services after SIGHUP
[2010/03/14 14:34:57,  3] param/loadparm.c:9016(lp_load_ex)
  lp_load_ex: refreshing parameters
Initialising global parameters
[2010/03/14 14:34:57,  3] ../lib/util/params.c:550(pm_process)
  params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
[2010/03/14 14:34:57,  3] param/loadparm.c:7703(do_section)
  Processing section "[global]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[stefano]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[carla]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[marcello]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[HTPC]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[public]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[DVD]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[private]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[Fantom]"
[2010/03/14 14:34:57,  3] param/loadparm.c:6174(lp_add_ipc)
  adding IPC service
[2010/03/14 14:34:57,  2] lib/interface.c:463(interpret_interface)
  interpret_interface: using netmask value 8 from config file on interface lo
[2010/03/14 14:34:57,  2] lib/interface.c:340(add_interface)
  added interface lo ip=127.0.0.1 bcast=127.255.255.255 netmask=255.0.0.0
[2010/03/14 14:34:57,  2] lib/interface.c:340(add_interface)
  added interface br0 ip=fe80::215:17ff:fec7:b3e5%br0 bcast=fe80::ffff:ffff:ffff:ffff%br0 netmask=ffff:ffff:ffff:ffff::
[2010/03/14 14:34:57,  2] lib/interface.c:340(add_interface)
  added interface br0 ip=192.168.100.200 bcast=192.168.100.255 netmask=255.255.255.0
[2010/03/14 14:34:57,  2] smbd/server.c:675(smbd_parent_loop)
  waiting for connections
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  1] smbd/process.c:755(smbd_sig_hup_handler)
  Reloading services after SIGHUP
[2010/03/14 14:34:57,  3] param/loadparm.c:9016(lp_load_ex)
  lp_load_ex: refreshing parameters
Initialising global parameters
[2010/03/14 14:34:57,  3] ../lib/util/params.c:550(pm_process)
  params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
[2010/03/14 14:34:57,  3] param/loadparm.c:7703(do_section)
  Processing section "[global]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[stefano]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[carla]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[marcello]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[HTPC]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[public]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[DVD]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[private]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[Fantom]"
[2010/03/14 14:34:57,  3] param/loadparm.c:6174(lp_add_ipc)
  adding IPC service
[2010/03/14 14:34:57,  2] lib/interface.c:463(interpret_interface)
  interpret_interface: using netmask value 8 from config file on interface lo
[2010/03/14 14:34:57,  2] lib/interface.c:340(add_interface)
  added interface lo ip=127.0.0.1 bcast=127.255.255.255 netmask=255.0.0.0
[2010/03/14 14:34:57,  2] lib/interface.c:340(add_interface)
  added interface br0 ip=fe80::215:17ff:fec7:b3e5%br0 bcast=fe80::ffff:ffff:ffff:ffff%br0 netmask=ffff:ffff:ffff:ffff::
[2010/03/14 14:34:57,  2] lib/interface.c:340(add_interface)
  added interface br0 ip=192.168.100.200 bcast=192.168.100.255 netmask=255.255.255.0[2010/03/14 14:33:35,  3] smbd/server.c:848(exit_server_common)
  Server exit (termination signal)
[2010/03/14 14:34:57,  0] smbd/server.c:1068(main)
  smbd version 3.4.0 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/03/14 14:34:57,  2] lib/tallocmsg.c:106(register_msg_pool_usage)
  Registered MSG_REQ_POOL_USAGE
[2010/03/14 14:34:57,  2] lib/dmallocmsg.c:77(register_dmalloc_msgs)
  Registered MSG_REQ_DMALLOC_MARK and LOG_CHANGED
[2010/03/14 14:34:57,  3] param/loadparm.c:9016(lp_load_ex)
  lp_load_ex: refreshing parameters
Initialising global parameters
[2010/03/14 14:34:57,  3] ../lib/util/params.c:550(pm_process)
  params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
[2010/03/14 14:34:57,  3] param/loadparm.c:7703(do_section)
  Processing section "[global]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[stefano]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[carla]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[marcello]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[HTPC]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[public]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[DVD]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[private]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[Fantom]"
[2010/03/14 14:34:57,  3] param/loadparm.c:6174(lp_add_ipc)
  adding IPC service
[2010/03/14 14:34:57,  2] lib/interface.c:463(interpret_interface)
  interpret_interface: using netmask value 8 from config file on interface lo
[2010/03/14 14:34:57,  2] lib/interface.c:340(add_interface)
  added interface lo ip=127.0.0.1 bcast=127.255.255.255 netmask=255.0.0.0
[2010/03/14 14:34:57,  2] lib/interface.c:340(add_interface)
  added interface br0 ip=fe80::215:17ff:fec7:b3e5%br0 bcast=fe80::ffff:ffff:ffff:ffff%br0 netmask=ffff:ffff:ffff:ffff::
[2010/03/14 14:34:57,  3] smbd/server.c:1110(main)
  loaded services
[2010/03/14 14:34:57,  3] smbd/server.c:1125(main)
  Becoming a daemon.
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 2
[2010/03/14 14:34:57,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 2
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] auth/token_util.c:433(create_local_nt_token)
  Failed to fetch domain sid for CUGIARISA
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] auth/token_util.c:464(create_local_nt_token)
  Failed to fetch domain sid for CUGIARISA
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] lib/privileges.c:63(get_privileges)
  get_privileges: No privileges assigned to SID [S-1-22-1-0]
[2010/03/14 14:34:57,  3] lib/privileges.c:63(get_privileges)
  get_privileges: No privileges assigned to SID [S-1-5-2]
[2010/03/14 14:34:57,  3] lib/privileges.c:63(get_privileges)
  get_privileges: No privileges assigned to SID [S-1-5-11]
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] auth/token_util.c:433(create_local_nt_token)
  Failed to fetch domain sid for CUGIARISA
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] auth/token_util.c:464(create_local_nt_token)
  Failed to fetch domain sid for CUGIARISA
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] lib/privileges.c:63(get_privileges)
  get_privileges: No privileges assigned to SID [S-1-5-21-2063038000-3907146246-2208747359-501]
[2010/03/14 14:34:57,  3] lib/privileges.c:63(get_privileges)
  get_privileges: No privileges assigned to SID [S-1-22-2-65534]
[2010/03/14 14:34:57,  3] lib/privileges.c:63(get_privileges)
  get_privileges: No privileges assigned to SID [S-1-5-2]
[2010/03/14 14:34:57,  3] lib/privileges.c:63(get_privileges)
  get_privileges: No privileges assigned to SID [S-1-5-32-546]
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:210(push_sec_ctx)
  push_sec_ctx(0, 0) : sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/uid.c:428(push_conn_ctx)
  push_conn_ctx(0) : conn_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 1
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:418(pop_sec_ctx)
  pop_sec_ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  3] printing/printing.c:1415(start_background_queue)
  start_background_queue: Starting background LPQ thread
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  1] smbd/process.c:755(smbd_sig_hup_handler)
  Reloading services after SIGHUP
[2010/03/14 14:34:57,  3] param/loadparm.c:9016(lp_load_ex)
  lp_load_ex: refreshing parameters
Initialising global parameters
[2010/03/14 14:34:57,  3] ../lib/util/params.c:550(pm_process)
  params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
[2010/03/14 14:34:57,  3] param/loadparm.c:7703(do_section)
  Processing section "[global]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[stefano]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[carla]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[marcello]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[HTPC]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[public]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[DVD]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[private]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[Fantom]"
[2010/03/14 14:34:57,  3] param/loadparm.c:6174(lp_add_ipc)
  adding IPC service
[2010/03/14 14:34:57,  2] lib/interface.c:463(interpret_interface)
  interpret_interface: using netmask value 8 from config file on interface lo
[2010/03/14 14:34:57,  2] lib/interface.c:340(add_interface)
  added interface lo ip=127.0.0.1 bcast=127.255.255.255 netmask=255.0.0.0
[2010/03/14 14:34:57,  2] lib/interface.c:340(add_interface)
  added interface br0 ip=fe80::215:17ff:fec7:b3e5%br0 bcast=fe80::ffff:ffff:ffff:ffff%br0 netmask=ffff:ffff:ffff:ffff::
[2010/03/14 14:34:57,  2] lib/interface.c:340(add_interface)
  added interface br0 ip=192.168.100.200 bcast=192.168.100.255 netmask=255.255.255.0
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  1] smbd/process.c:755(smbd_sig_hup_handler)
  Reloading services after SIGHUP
[2010/03/14 14:34:57,  3] param/loadparm.c:9016(lp_load_ex)
  lp_load_ex: refreshing parameters
Initialising global parameters
[2010/03/14 14:34:57,  3] ../lib/util/params.c:550(pm_process)
  params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
[2010/03/14 14:34:57,  3] param/loadparm.c:7703(do_section)
  Processing section "[global]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[stefano]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[carla]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[marcello]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[HTPC]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[public]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[DVD]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[private]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[Fantom]"
[2010/03/14 14:34:57,  3] param/loadparm.c:6174(lp_add_ipc)
  adding IPC service
[2010/03/14 14:34:57,  2] lib/interface.c:463(interpret_interface)
  interpret_interface: using netmask value 8 from config file on interface lo
[2010/03/14 14:34:57,  2] lib/interface.c:340(add_interface)
  added interface lo ip=127.0.0.1 bcast=127.255.255.255 netmask=255.0.0.0
[2010/03/14 14:34:57,  2] lib/interface.c:340(add_interface)
  added interface br0 ip=fe80::215:17ff:fec7:b3e5%br0 bcast=fe80::ffff:ffff:ffff:ffff%br0 netmask=ffff:ffff:ffff:ffff::
[2010/03/14 14:34:57,  2] lib/interface.c:340(add_interface)
  added interface br0 ip=192.168.100.200 bcast=192.168.100.255 netmask=255.255.255.0
[2010/03/14 14:34:57,  2] smbd/server.c:675(smbd_parent_loop)
  waiting for connections
[2010/03/14 14:34:57,  3] smbd/sec_ctx.c:310(set_sec_ctx)
  setting sec ctx (0, 0) - sec_ctx_stack_ndx = 0
[2010/03/14 14:34:57,  1] smbd/process.c:755(smbd_sig_hup_handler)
  Reloading services after SIGHUP
[2010/03/14 14:34:57,  3] param/loadparm.c:9016(lp_load_ex)
  lp_load_ex: refreshing parameters
Initialising global parameters
[2010/03/14 14:34:57,  3] ../lib/util/params.c:550(pm_process)
  params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
[2010/03/14 14:34:57,  3] param/loadparm.c:7703(do_section)
  Processing section "[global]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[stefano]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[carla]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[marcello]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[HTPC]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[public]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[DVD]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[private]"
[2010/03/14 14:34:57,  2] param/loadparm.c:7720(do_section)
  Processing section "[Fantom]"
[2010/03/14 14:34:57,  3] param/loadparm.c:6174(lp_add_ipc)
  adding IPC service
[2010/03/14 14:34:57,  2] lib/interface.c:463(interpret_interface)
  interpret_interface: using netmask value 8 from config file on interface lo
[2010/03/14 14:34:57,  2] lib/interface.c:340(add_interface)
  added interface lo ip=127.0.0.1 bcast=127.255.255.255 netmask=255.0.0.0
[2010/03/14 14:34:57,  2] lib/interface.c:340(add_interface)
  added interface br0 ip=fe80::215:17ff:fec7:b3e5%br0 bcast=fe80::ffff:ffff:ffff:ffff%br0 netmask=ffff:ffff:ffff:ffff::
[2010/03/14 14:34:57,  2] lib/interface.c:340(add_interface)
  added interface br0 ip=192.168.100.200 bcast=192.168.100.255 netmask=255.255.255.0
```

Any help appreciated.

Thanks

---

### Post by redmk2 on 2010-03-14
> **ris8 said:**
> I have a file server running samba 3.4.0. I just upgraded ubuntu to 9.10. The upgrade was unfortunately stopped in the middle, but I think I managed to complete it.
The problem is that now samba will not work after a reboot. The daemons are running, but any attempt to connect from a windows machine fails (Windows 7: the network path was not found). Manually restarting the service fixes the problem, but I need a more stable solution!
Interestingly, I can ssh to the machine, or rdp to a virtual machine running on it.

The logs don't seem to report any error:

```
stefano@SERVER02:/var/log/samba$ tail log.smbd
[2010/03/14 04:02:11,  0] smbd/server.c:1068(main)
  smbd version 3.4.0 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/03/14 04:02:15,  1] smbd/process.c:755 smbd_sig_hup_handler)
  Reloading services after SIGHUP

stefano@SERVER02:/var/log/samba$ tail log.nmbd
[2010/03/14 04:02:11,  0] nmbd/nmbd_subnetdb.c:206(create_subnets)
  create_subnets: No local IPv4 non-loopback interfaces !
[2010/03/14 04:02:11,  0] nmbd/nmbd_subnetdb.c:207(create_subnets)
  create_subnets: Waiting for an interface to appear ...
[2010/03/14 04:02:40,  0] nmbd/nmbd_become_lmb.c:395(become_local_master_stage2)
  *****

  Samba name server SERVER02 is now a local master browser for workgroup CUGIARISA on subnet 192.168.100.200

  *****
```
...

These would bother me.  They do not appear in my logs.

```
[COLOR="Red"][B]2010/03/14 04:02:15,  1] smbd/process.c:755 smbd_sig_hup_handler)
  Reloading services after SIGHUP

...

nmbd/nmbd_subnetdb.c:207(create_subnets)
  create_subnets: Waiting for an interface to appear ...[/B][/COLOR]
```


> The console shows a reloading samba, smb.conf only and a restarting ssh. It shows these messages right *after* it asks for a login. A little web search this may be related to dhcp acquiring a new ip. Not sure this is even an issue as I never use the console so I don't know if it's normal.


The console output is the [FONT="Courier New"]stderr[/FONT] output location.  All errors are by default directed there unless directed someplace else.  It has nothing to do with YOU using the console.

It sure looks like this is a timing problem.  If the smbd/nmbd daemons start before there is an address they will die.  Therefore it is logical that after your dhcp service is started, the smbd/nmbd is the reloaded successfully when you manually restart them.

Why use dhcp for the server anyway?  This creates all kinds of problems for servers in general and Samba in particular.  [[COLOR="Navy"]**_See here for info._**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1140094")

---

### Post by ris8 on 2010-03-14
Wow, switching to a static ip in /etc/netowrk/interfaces did the trick! I always thought asking the dhcp server to keep the server address static was enough...

Not sure I understand what was happening... maybe dhcp server was slow to respond and samba did not initialize properly... anyhow, thanks!

---

### Post by redmk2 on 2010-03-14
> **ris8 said:**
> Wow, switching to a static ip in /etc/netowrk/interfaces did the trick! I always thought asking the dhcp server to keep the server address static was enough...

A dhcp served IP address always on a lease.  It is not static at all.  The IP address is ***reserved*** (filtered by MAC address) and therefore unchanging.
  
> 

Not sure I understand what was happening... maybe dhcp server was slow to respond and samba did not initialize properly... anyhow, thanks!

The IP address is only *part *of the lease.  The request for a dhcp served IP address comes from the client.  The client requests and the server responds.  By it's nature it takes some amount of time.

---

