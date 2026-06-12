---
title: "SGE cannot run in PE &quot;&quot; because it only offers 0 slots"
date: 2013-04-14
forum: Server Platforms
---

### Post by libranjie on 2013-04-14
Hello guys,

I have already set up an parallel environment with ubuntu server, 

```

$ qconf -sp cluster-pe
pe_name            cluster-pe
slots              100
user_lists         NONE
xuser_lists        NONE
start_proc_args    /bin/true
stop_proc_args     /bin/true
allocation_rule    $pe_slots
control_slaves     FALSE
job_is_first_task  TRUE
urgency_slots      min
accounting_summary FALSE

```

The queue 

```

$ qconf -sq libranjie.q
qname                 libranjie.q
hostlist              @libranjie
seq_no                0
load_thresholds       np_load_avg=1.75
suspend_thresholds    NONE
nsuspend              1
suspend_interval      00:05:00
priority              0
min_cpu_interval      00:05:00
processors            UNDEFINED
qtype                 BATCH INTERACTIVE
ckpt_list             NONE
pe_list               cluster-pe make
rerun                 FALSE
slots                 1,[ubuntu-client03=12],[ubuntu-client04=12], \
                      [ubuntu-client05=12],[ubuntu-client06=12], \
                      [ubuntu-client07=12],[ubuntu-client08=12], \
                      [ubuntu-client09=12],[ubuntu-client10=12]
tmpdir                /tmp
shell                 /bin/bash
prolog                NONE
epilog                NONE
shell_start_mode      posix_compliant
starter_method        NONE
suspend_method        NONE
resume_method         NONE
terminate_method      NONE
notify                00:00:60
owner_list            NONE
user_lists            NONE
xuser_lists           NONE
subordinate_list      NONE
complex_values        NONE
projects              NONE
xprojects             NONE
calendar              NONE
initial_state         default
s_rt                  INFINITY
h_rt                  INFINITY
s_cpu                 INFINITY
h_cpu                 INFINITY
s_fsize               INFINITY
h_fsize               INFINITY
s_data                INFINITY
h_data                INFINITY
s_stack               INFINITY
h_stack               INFINITY
s_core                INFINITY
h_core                INFINITY
s_rss                 INFINITY
h_rss                 INFINITY
s_vmem                INFINITY
h_vmem                INFINITY

```

But as i qsub job, 

```

$ qstat -j 899 |tail -8
parallel environment:  cluster-pe range: 23
scheduling info:            queue instance "libranjie.q@ubuntu-client03" dropped because it is temporarily not available
                            queue instance "libranjie.q@ubuntu-client04" dropped because it is temporarily not available
                            queue instance "libranjie.q@ubuntu-client05" dropped because it is temporarily not available
                            queue instance "libranjie.q@ubuntu-client06" dropped because it is temporarily not available
                            queue instance "libranjie.q@ubuntu-client07" dropped because it is temporarily not available
                            queue instance "libranjie.q@ubuntu-client08" dropped because it is temporarily not available
                            cannot run in PE "cluster-pe" because it only offers 0 slots

```

The queue status is:

```

$ qstat -f
queuename                      qtype resv/used/tot. load_avg arch          states
---------------------------------------------------------------------------------
libranjie.q@ubuntu-client03    BIP   0/0/12         -NA-     lx26-amd64    au
---------------------------------------------------------------------------------
libranjie.q@ubuntu-client04    BIP   0/0/12         -NA-     lx26-amd64    au
---------------------------------------------------------------------------------
libranjie.q@ubuntu-client05    BIP   0/0/12         -NA-     lx26-amd64    au
---------------------------------------------------------------------------------
libranjie.q@ubuntu-client06    BIP   0/0/12         -NA-     lx26-amd64    au
---------------------------------------------------------------------------------
libranjie.q@ubuntu-client07    BIP   0/0/12         -NA-     lx26-amd64    au
---------------------------------------------------------------------------------
libranjie.q@ubuntu-client08    BIP   0/0/12         -NA-     lx26-amd64    au
---------------------------------------------------------------------------------
libranjie.q@ubuntu-client09    BIP   0/0/12         0.01     lx26-amd64    
---------------------------------------------------------------------------------
libranjie.q@ubuntu-client10    BIP   0/0/12         0.01     lx26-amd64    

############################################################################
 - PENDING JOBS - PENDING JOBS - PENDING JOBS - PENDING JOBS - PENDING JOBS
############################################################################
    899 0.50000 rCA_asm_01 ubuntu       qw    04/14/2013 15:17:36    23 

```

Comment, the client03-client08 is power off.
Any one can help to make the parallel environment work?

---

### Post by libranjie on 2013-04-21
[FONT=garamond]I have made mistake on how to manage my clsuter.
When use parallel environment, the client node need to have thr right to use qrsh.
That's means we need to install gridengine-client

```
#apt-get install gridengine-client
```[/FONT]

---

