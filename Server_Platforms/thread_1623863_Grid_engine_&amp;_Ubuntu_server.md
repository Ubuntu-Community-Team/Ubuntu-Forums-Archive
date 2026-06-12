---
title: "Grid engine &amp; Ubuntu server"
date: 2010-11-17
forum: Server Platforms
---

### Post by jokemach on 2010-11-17
Hi,

I'm running Ubuntu 10.04.1 LTS (2.6.32-21-server kernel) on three 64-bit quad core machines where I'm now trying to install sun grid engine.  I followed this guide ([http://pka.engr.ccny.cuny.edu/~jmao/node/49]("http://pka.engr.ccny.cuny.edu/%7Ejmao/node/49")) but was still unable to submit jobs.

The master is located on host "albert", the first slave on "david" and the second slave on "tex". I've made sure that the /etc/hostname and /etc/hosts are both correct. Furthermore in executing the qping command on each slave I get the following:

david:
    qping -info albert 6444 qmaster 1
        11/17/2010 11:31:42:
        SIRM version:             0.1
        SIRM message id:          1
        start time:               11/12/2010 15:26:11 (1289571971)
        run time [s]:             417931
        messages in read buffer:  0
        messages in write buffer: 0
        nr. of connected clients: 1
        status:                   1
        info:                     MAIN: E (417930.66) | signaler000: E (417930.60) | event_master000: E (0.39) | timer000: E (0.39) | worker000: E (5.39) | worker001: E (5.39) | listener000: E (2.30) | listener001: E (3.30) | scheduler000: E (5.39) | WARNING
        malloc:                   arena(0) |ordblks(1) | smblks(0) | hblksr(0) | hblhkd(0) usmblks(0) | fsmblks(0) | uordblks(0) | fordblks(0) | keepcost(0)
        Monitor:                  disabled

tex:
    qping -info albert 6444 qmaster 1
        11/17/2010 11:38:12:
        SIRM version:             0.1
        SIRM message id:          1
        start time:               11/12/2010 15:26:11 (1289571971)
        run time [s]:             418320
        messages in read buffer:  0
        messages in write buffer: 0
        nr. of connected clients: 1
        status:                   1
        info:                     MAIN: E (418320.24) | signaler000: E (418320.18) | event_master000: E (0.98) | timer000: E (0.98) | worker000: E (4.98) | worker001: E (4.98) | listener000: E (1.83) | listener001: E (2.83) | scheduler000: E (4.98) | WARNING
        malloc:                   arena(0) |ordblks(1) | smblks(0) | hblksr(0) | hblhkd(0) usmblks(0) | fsmblks(0) | uordblks(0) | fordblks(0) | keepcost(0)
        Monitor:                  disabled

In submitting a dummy job (echo "hello" stored in bash script test.sh) using "qsub test.sh" I get the following table from "qstat"...

job-ID  prior   name       user         state submit/start at     queue                          slots ja-task-ID 
-----------------------------------------------------------------------------------------------------------------
      5 0.00000 test.sh    jokemach       qw    11/17/2010 11:41:57                                    1

... and "qstat -j 5" gives:
==============================================================
job_number:                 5
exec_file:                  job_scripts/5
submission_time:            Wed Nov 17 11:41:57 2010
owner:                      jokemach
uid:                        1004
group:                      jokemach
gid:                        1004
sge_o_home:                 /kerberos/users/jokemach
sge_o_log_name:             jokemach
sge_o_path:                 /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
sge_o_shell:                /bin/bash
sge_o_workdir:              /kerberos/users/jokemach
sge_o_host:                 albert
account:                    sge
mail_list:                  jokemach@albert
notify:                     FALSE
job_name:                   test.sh
jobshare:                   0
env_list:                   
script_file:                test.sh
scheduling info:            queue instance "test@david" dropped because it is temporarily not available
                            queue instance "test@tex" dropped because it is temporarily not available
                            All queues dropped because of overload or full


---------------------------------

Any suggestions on how to proceed?

Thanks!

---

