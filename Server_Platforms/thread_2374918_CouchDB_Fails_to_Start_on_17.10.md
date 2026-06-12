---
title: "CouchDB Fails to Start on 17.10"
date: 2017-10-20
forum: Server Platforms
---

### Post by paranoidcoder on 2017-10-20
First of all, I apologize if this is not the correct forum for this kind of question as I have not participated in these forums very much. Ubuntu 17.10 has been a smooth upgrade for the most part, however I seem to be having issues using CouchDB. When checking the status of the CouchDB systemd service I get this:
 ```
&#9679; couchdb.service - System-wide CouchDB instance
   Loaded: loaded (/lib/systemd/system/couchdb.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Fri 2017-10-20 06:41:53 CDT; 29s ago
  Process: 970 ExecStart=/usr/bin/couchdb (code=exited, status=1/FAILURE)
 Main PID: 970 (code=exited, status=1/FAILURE)

Oct 20 06:41:53 devin-VirtualBox systemd[1]: couchdb.service: Main process exited, code=exited, status=1/FAILURE
Oct 20 06:41:53 devin-VirtualBox systemd[1]: couchdb.service: Unit entered failed state.
Oct 20 06:41:53 devin-VirtualBox systemd[1]: couchdb.service: Failed with result 'exit-code'.
Oct 20 06:41:53 devin-VirtualBox systemd[1]: couchdb.service: Service hold-off time over, scheduling restart.
Oct 20 06:41:53 devin-VirtualBox systemd[1]: Stopped System-wide CouchDB instance.
Oct 20 06:41:53 devin-VirtualBox systemd[1]: couchdb.service: Start request repeated too quickly.
Oct 20 06:41:53 devin-VirtualBox systemd[1]: Failed to start System-wide CouchDB instance.
Oct 20 06:41:53 devin-VirtualBox systemd[1]: couchdb.service: Unit entered failed state.
Oct 20 06:41:53 devin-VirtualBox systemd[1]: couchdb.service: Failed with result 'exit-code'.
```

If I try to run `sudo couchdb` I get this:
```
Apache CouchDB 1.6.0 (LogLevel=info) is starting.
[error] [<0.123.0>] {error_report,<0.59.0>,
                     {<0.123.0>,supervisor_report,
                      [{supervisor,{local,couch_secondary_**********},
                       {errorContext,start_error},
                       {reason,
                        {'EXIT',
                         {undef,
                          [{crypto,rand_bytes,[16],[]},
                           {couch_uuids,random,0,
                            [{file,"couch_uuids.erl"},{line,33}]},
                           {couch_server,get_uuid,0,
                            [{file,"couch_server.erl"},{line,54}]},
                           {couch_httpd,start_link,2,
                            [{file,"couch_httpd.erl"},{line,119}]},
                           {supervisor,do_start_child,2,
                            [{file,"supervisor.erl"},{line,365}]},
                           {supervisor,start_children,3,
                            [{file,"supervisor.erl"},{line,348}]},
                           {supervisor,init_children,2,
                            [{file,"supervisor.erl"},{line,314}]},
                           {gen_server,init_it,2,
                            [{file,"gen_server.erl"},{line,365}]}]}}},
                       {offender,
                        [{pid,undefined},
                         {id,httpd},
                         {mfargs,{couch_httpd,start_link,[]}},
                         {restart_type,permanent},
                         {shutdown,brutal_kill},
                         {child_type,worker}]}]}}

=SUPERVISOR REPORT==== 20-Oct-2017::06:43:50 ===
     Supervisor: {local,couch_secondary_**********
     Context:    start_error
     Reason:     {'EXIT',
                     {undef,
                         [{crypto,rand_bytes,[16],[]},
                          {couch_uuids,random,0,
                              [{file,"couch_uuids.erl"},{line,33}]},
                          {couch_server,get_uuid,0,
                              [{file,"couch_server.erl"},{line,54}]},
                          {couch_httpd,start_link,2,
                              [{file,"couch_httpd.erl"},{line,119}]},
                          {supervisor,do_start_child,2,
                              [{file,"supervisor.erl"},{line,365}]},
                          {supervisor,start_children,3,
                              [{file,"supervisor.erl"},{line,348}]},
                          {supervisor,init_children,2,
                              [{file,"supervisor.erl"},{line,314}]},
                          {gen_server,init_it,2,
                              [{file,"gen_server.erl"},{line,365}]}]}}
     Offender:   [{pid,undefined},
                  {id,httpd},
                  {mfargs,{couch_httpd,start_link,[]}},
                  {restart_type,permanent},
                  {shutdown,brutal_kill},
                  {child_type,worker}]

{"init terminating in do_boot",{{badmatch,{error,{bad_return,{{couch_app,start,[normal,["/etc/couchdb/default.ini","/etc/couchdb/local.ini"]]},{'EXIT',{{badmatch,{error,{shutdown,{failed_to_start_child,couch_secondary_services,{shutdown,{failed_to_start_child,httpd,{'EXIT',{undef,[{crypto,rand_bytes,[16],[]},{couch_uuids,random,0,[{file,"couch_uuids.erl"},{line,33}]},{couch_server,get_uuid,0,[{file,"couch_server.erl"},{line,54}]},{couch_httpd,start_link,2,[{file,"couch_httpd.erl"},{line,119}]},{supervisor,do_start_child,2,[{file,"supervisor.erl"},{line,365}]},{supervisor,start_children,3,[{file,"supervisor.erl"},{line,348}]},{supervisor,init_children,2,[{file,"supervisor.erl"},{line,314}]},{gen_server,init_it,2,[{file,"gen_server.erl"},{line,365}]}]}}}}}}}},[{couch_server_sup,start_server,1,[{file,"couch_server_sup.erl"},{line,98}]},{application_master,start_it_old,4,[{file,"application_master.erl"},{line,273}]}]}}}}}},[{couch,start,0,[{file,"couch.erl"},{line,18}]},{init,start_em,1,[]},{init,do_boot,3,[]}]}}
init terminating in do_boot ({{badmatch,{error,{bad_return,{_}}}},[{couch,start,0,[{_},{_}]},{init,start_em,1,[]},{init,do_boot,3,[]}]})

Crash dump is being written to: erl_crash.dump...done
```

I also tried grabbing the Debian/Ubuntu repo from the Apache CouchDB website, but they don't have a 17.10 build available yet so no luck there.

Anyone have any ideas? Thanks in advance.

EDIT
I have created a GitHub issue with CouchDB, and I have filed a bug on Launchpad for the CouchDB package:
[https://github.com/apache/couchdb/issues/910](https://github.com/apache/couchdb/issues/910)
[https://bugs.launchpad.net/ubuntu/+source/couchdb/+bug/1729305](https://bugs.launchpad.net/ubuntu/+source/couchdb/+bug/1729305)

EDIT 2
A System76 engineer has created a PPA with CouchDB 1.7.0 that works on Ubuntu 17.10: [https://launchpad.net/~jderose/+archive/ubuntu/couchdb-1.7.0](https://launchpad.net/~jderose/+archive/ubuntu/couchdb-1.7.0)

---

### Post by ajgreeny on 2017-10-20
*Thread moved to **Virtualisation**.* which is more appropriate and a better fit.

---

### Post by paranoidcoder on 2017-10-20
> **ajgreeny said:**
> *Thread moved to **Virtualisation**.* which is more appropriate and a better fit.
Can I ask why? CouchDB is a no-SQL database and front end access to this no-SQL database and has nothing to do with virtualization as far as I know.

---

### Post by mgscox on 2017-10-20
Same problem.

CouchDb won't start after upgrade to 17.10 and throwing error that seems to relate to couch_uuids.
Beyond that I don't have the faintest idea how to get it working again

```

[error] [<0.174.0>] {error_report,<0.59.0>,
                     {<0.174.0>,crash_report,
                      [[{initial_call,{couch_uuids,init,['Argument__1']}},
                        {pid,<0.174.0>},
                        {registered_name,[]},
                        {error_info,
                         {error,undef,
                          [{crypto,rand_bytes,"\r",[]},
                           {couch_uuids,new_prefix,0,
                            [{file,"couch_uuids.erl"},{line,84}]},
                           {couch_uuids,state,0,
                            [{file,"couch_uuids.erl"},{line,100}]},
                           {couch_uuids,init,1,
                            [{file,"couch_uuids.erl"},{line,50}]},
                           {gen_server,init_it,2,
                            [{file,"gen_server.erl"},{line,365}]},
                           {gen_server,init_it,6,
                            [{file,"gen_server.erl"},{line,333}]},
                           {proc_lib,init_p_do_apply,3,
                            [{file,"proc_lib.erl"},{line,247}]}]}},
                        {ancestors,
                         [couch_secondary_services,couch_server_sup,<0.60.0>]},
                        {message_queue_len,0},
                        {messages,[]},
                        {links,[<0.123.0>]},
                        {dictionary,[]},
                        {trap_exit,false},
                        {status,running},
                        {heap_size,610},
                        {stack_size,27},
                        {reductions,234}],
                       []]}}
{"init terminating in do_boot",{{badmatch,{error,{bad_return,{{couch_app,start,[normal,["/etc/couchdb/default.ini","/etc/couchdb/local.ini"]]},{'EXIT',{{badmatch,{error,{shutdown,{failed_to_start_child,couch_secondary_services,{shutdown,{failed_to_start_child,uu",[]},{couch_uuids,new_prefix,0,[{file,"couch_uuids.erl"},{line,84}]},{couch_uuids,state,0,[{file,"couch_uuids.erl"},{line,100}]},{couch_uuids,init,1,[{file,"couch_uuids.erl"},{line,50}]},{gen_server,init_it,2,[{file,"gen_server.erl"},{line,365}]},{gen_server,init_it,6,[{file,"gen_server.erl"},{line,333}]},{proc_lib,init_p_do_apply,3,[{file,"proc_lib.erl"},{line,247}]}]}}}}}}},[{couch_server_sup,start_server,1,[{file,"couch_server_sup.erl"},{line,98}]},{application_master,start_it_old,4,[{file,"application_master.erl"},{line,273}]}]}}}}}},[{couch,start,0,[{file,"couch.erl"},{line,18}]},{init,start_em,1,[]},{init,do_boot,3,[]}]}}
init terminating in do_boot ({{badmatch,{error,{bad_return,{_}}}},[{couch,start,0,[{_},{_}]},{init,start_em,1,[]},{init,do_boot,3,[]}]})

```

---

### Post by ajgreeny on 2017-10-20
The thread was moved as it appears to be a problem in an OS running as a VM in VirtualBox; correct?

As such the forum default placement is that it should sit in the Virtualisation forum.

Regrettably I do not know about CouchDB so can not help with that problem.

---

### Post by paranoidcoder on 2017-10-20
> **ajgreeny said:**
> The thread was moved as it appears to be a problem in an OS running as a VM in VirtualBox; correct?

As such the forum default placement is that it should sit in the Virtualisation forum.

Regrettably I do not know about CouchDB so can not help with that problem.
No, I do not believe I mentioned anything about a VM. This happens on my main machine running on bare metal, though I have tested it in a VM as well to be sure it was nothing to do with my system configuration, but the main issue is not VM related whatsoever.

---

### Post by ajgreeny on 2017-10-20
OK, after discussion with others, and your comment about the problem also occurring on bare metal installed systems, I have moved this back to the servers forum.

---

### Post by paranoidcoder on 2017-10-20
Awesome, thank you very much.

---

### Post by paranoidcoder on 2017-10-23
I have created a CouchDB issue on Apache's GitHub, so feel free to comment if you're experiencing the same issue. [https://github.com/apache/couchdb/issues/910](https://github.com/apache/couchdb/issues/910)

---

### Post by paranoidcoder on 2017-11-01
The CouchDB GitHub issue has been closed. The issue lies with Ubuntu's choice to upgrade the version of Erlang shipping on 17.10. I have filed a bug with the couchdb package on Launchpad here: [https://bugs.launchpad.net/ubuntu/+source/couchdb/+bug/1729305](https://bugs.launchpad.net/ubuntu/+source/couchdb/+bug/1729305)

---

### Post by paranoidcoder on 2017-11-02
A System76 engineer has created a PPA with CouchDB 1.7.0 that works on Ubuntu 17.10: [https://launchpad.net/~jderose/+archive/ubuntu/couchdb-1.7.0](https://launchpad.net/~jderose/+archive/ubuntu/couchdb-1.7.0), I think this thread could now be marked as solved.

---

### Post by darkod on 2017-11-03
Only you or an admin can mark it solved. You can do that in Thread Tools above the first post, if you don't need more help.

Thanks.

---

### Post by paranoidcoder on 2017-11-06
Awesome, thank you. The thread is marked as solved and all is good in the world.

---

