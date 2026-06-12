---
title: "Kernel Memory Consumption Issue Around AuditD Implementation"
date: 2022-09-21
forum: Security
---

### Post by murchisonc on 2022-09-21
Hi,

Recently i was trying to satisfy our internal company requirements to log all user executions on systems, in terms of auditing, on our newly installed Ubuntu 22.04 LTS VM's (We are moving from CentOS, but that is not too relevant here) and so i set up auditd with a selection of rules to filter out just what we require. This works fine in terms of the actual messages being filtered and collected but something i did not expect was a gradual kernel memory consumption over time on a few Ubuntu units. This only seemed to be happening on a few units so i looked on those systems to identify what is different and it seems the main difference there are shell scripts being executed frequently on these systems which tend to generate a fair amount of audit entries.

So the example system i wish to present here is one of our internal nameservers (Bind9). Basically in our infrastructure we have a "DNS zone manager" worker script that executes every minute via cron to perform various zone management operations. Obviously every execution in this script is being audited (And i have not found a way to easily filter out "tty=(none)" messages yet, which is something i would like to do but that is separate to my initial question) which does generate frequent message bursts. Here is an example auditd message count over 5 consecutive minutes broken down by each minute:



root@ns112prd:/etc/audit/plugins.d# ausearch --start 21/09/22 15:00 --end 21/09/22 15:01 | egrep '^type=' | wc -l
1080
root@ns112prd:/etc/audit/plugins.d# ausearch --start 21/09/22 15:01 --end 21/09/22 15:02 | egrep '^type=' | wc -l
1080
root@ns112prd:/etc/audit/plugins.d# ausearch --start 21/09/22 15:02 --end 21/09/22 15:03 | egrep '^type=' | wc -l
1080
root@ns112prd:/etc/audit/plugins.d# ausearch --start 21/09/22 15:03 --end 21/09/22 15:04 | egrep '^type=' | wc -l
1088
root@ns112prd:/etc/audit/plugins.d# ausearch --start 21/09/22 15:04 --end 21/09/22 15:05 | egrep '^type=' | wc -l
1080

So a steady amount of messages a minute there. The seeming consistency in count is from the same script executing on a precise frequent schedule and everything else being somewhat static (In terms of executions) on the system. This can be broken down into the following message types over 5 minutes:

root@ns112prd:/etc/audit/plugins.d# ausearch --start 21/09/22 15:00 --end 21/09/22 15:05 | egrep '^type=' | awk -F'type=' '{print $2}' | awk '{print $1}' | sort | uniq -c


   1352 CWD
   1352 EXECVE
   1352 PROCTITLE
   1352 SYSCALL


This is expected and i do already have some ruling to prune some things we do not want:

[/etc/audit/rules.d/75-allcmd.rules]

-D
-b 32768
-f 1
-a always,exit -F arch=b64 -S connect -F exe=/usr/sbin/sshd -F exit=-EINPROGRESS -F key=SSHD_CONNECTION
-a always,exit -F arch=b64 -S execve -F key=USER_COMMAND
-a always,exit -F arch=b32 -S connect -F exe=/usr/sbin/sshd -F exit=-EINPROGRESS -F key=SSHD_CONNECTION
-a always,exit -F arch=b32 -S execve -F key=USER_COMMAND
-a never,exclude -F msgtype=CRYPTO_KEY_USER
-a never,exclude -F msgtype=PATH
-a never,exclude -F msgtype=1421
-a never,exclude -F exe=/usr/sbin/cron
-a never,exclude -F exe=/usr/bin/logger
-a never,exclude -F exe=/usr/bin/dash
-a never,exclude -F auid=-1

Now to the problem. It seems with this set up (And this does not happen as readily on other Ubuntu units with the same auditd configuration, but most systems with Ubuntu currently have no cron jobs... so that is the main difference here) the memory on affected systems slowly gets sapped to the point of exhaustion (Takes about 36 - 48 hours for 4GB to be depleted to critical levels). A look into this shows this is being consumed in kernel memory, more specifically the kernel slab kmalloc-2k. This slab seems to continue to grow out of proportion. Here is output showing it is currently 

 Active / Total Objects (% used)    : 625148 / 628922 (99.4%)
 Active / Total Slabs (% used)      : 30432 / 30432 (100.0%)
 Active / Total Caches (% used)     : 114 / 182 (62.6%)
 Active / Total Size (% used)       : 488860.04K / 490382.59K (99.7%)
 Minimum / Average / Maximum Object : 0.01K / 0.78K / 8.00K


  OBJS ACTIVE  USE OBJ SIZE  SLABS OBJ/SLAB CACHE SIZE NAME                   
 60650  60644  99%    6.00K  12130        5    388160K kmalloc-2k             
 43725  43617  99%    0.62K   1749       25     27984K inode_cache            
 63008  62958  99%    0.25K   3938       16     15752K skbuff_head_cache      
 26208  26058  99%    0.50K   1638       16     13104K kmalloc-512            
 66696  66374  99%    0.19K   3176       21     12704K dentry

This is massive against what i see on our other systems (And it only gets bigger over time). To me this then either looks like some issue with constantly overloaded auditd queues or some sort of memory leak (Don't really want to jump to a memory leak right away as i may be missing something here). Thing is auditd looks as if it is gathering messages fine so i am not entirely sure what is going on here (NB: I started with a low auditd buffer count and have gone up to 32768 gradually, but there was no real change to this memory consumption pattern).

For disclosure our auditd.conf is pretty standard here (Just increased the queue depth too to see if that had any effect, but not too much):

[/etc/audit/auditd.conf]

local_events = yes
write_logs = yes
log_file = /var/log/audit/audit.log
log_group = adm
log_format = ENRICHED
flush = INCREMENTAL_ASYNC
freq = 50
max_log_file = 8
num_logs = 5
priority_boost = 4
name_format = NONE
##name = mydomain
max_log_file_action = ROTATE
space_left = 75
space_left_action = SYSLOG
verify_email = yes
action_mail_acct = root
admin_space_left = 50
admin_space_left_action = SUSPEND
disk_full_action = SUSPEND
disk_error_action = SUSPEND
use_libwrap = yes
##tcp_listen_port = 60
tcp_listen_queue = 5
tcp_max_per_addr = 100
##tcp_client_ports = 1024-65535
tcp_client_max_idle = 0
transport = TCP
krb5_principal = auditd
##krb5_key_file = /etc/audit/audit.key
distribute_network = no
q_depth = 32768
overflow_action = SYSLOG
max_restarts = 10
plugin_dir = /etc/audit/plugins.d
end_of_event_timeout = 2

I am wondering if anyone has seen this before in the wild and can indicate what may be going on here as i am unsure after looking for a few days. I am aware that auditd can be a bit heavy as it hooks into the kernel in realtime (I believe) but i would have thought ~1000 messages a minute could be handled (They do burst when the script executes though).

We simply cannot satisfy this security compliance requirement with auditd if it leads to inevitable memory exhaustion on systems via kernel memory.

I just want to add (In case it is useful information) that apparmor is disabled on our Ubuntu units completely (From GRUB boot).

If anyone has any ideas then i am open to them.

Thanks,

Christopher Murchison

---

