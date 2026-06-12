---
title: "Apache PHP Segmentation Fault: CoreDump analysis"
date: 2016-02-06
forum: Server Platforms
---

### Post by GZW on 2016-02-06
Hi,

after upgrade from Ubuntu 12.04 LTS to Ubuntu 14.04 LTS, I often receive Apache segmentation faults.
I already set CoreDumpDirectory to /tmp/apache2-gdb-dump
```

 [core:notice] [pid 4383] AH00051: child pid 31773 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump

```
I tried to analyize the dump
```
gdb /usr/sbin/apache2 /tmp/apache2-gdb-dump/core
```
backtrace full:
```

#0  0x00007f8df19d0df6 in ?? () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#1  0x00007f8df19d0f8c in ?? () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#2  0x00007f8df19e8470 in _zval_ptr_dtor () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#3  0x00007f8df19ed42f in destroy_zend_class () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#4  0x00007f8df1a06008 in zend_hash_clean () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#5  0x00007f8deead0a31 in accel_shutdown () from /usr/lib/php5/20121212/opcache.so
No symbol table info available.
#6  0x00007f8deead5050 in ?? () from /usr/lib/php5/20121212/opcache.so
No symbol table info available.
#7  0x00007f8df19ff633 in module_destructor () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#8  0x00007f8df1a048e5 in ?? () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#9  0x00007f8df1a060e8 in zend_hash_graceful_reverse_destroy () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#10 0x00007f8df19f80be in zend_shutdown () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#11 0x00007f8df199983b in php_module_shutdown () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#12 0x00007f8df19998f9 in php_module_shutdown_wrapper () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#13 0x00007f8df1aa8f61 in ?? () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#14 0x00007f8df56979ce in apr_pool_destroy () from /usr/lib/x86_64-linux-gnu/libapr-1.so.0
No symbol table info available.
#15 0x00007f8df23c91ae in ?? () from /usr/lib/apache2/modules/mod_mpm_prefork.so
No symbol table info available.
#16 0x00007f8df23c91eb in ?? () from /usr/lib/apache2/modules/mod_mpm_prefork.so
No symbol table info available.
#17 <signal handler called>
No locals.
#18 0x00007f8df518582d in read () at ../sysdeps/unix/syscall-template.S:81
No locals.
#19 0x00007f8de58b3944 in vio_read_buff () from /usr/lib/x86_64-linux-gnu/libmysqlclient.so.18
No symbol table info available.
#20 0x00007f8de58a3dae in ?? () from /usr/lib/x86_64-linux-gnu/libmysqlclient.so.18
No symbol table info available.
#21 0x00007f8de58a48cd in my_net_read () from /usr/lib/x86_64-linux-gnu/libmysqlclient.so.18
No symbol table info available.
#22 0x00007f8de589dd6c in cli_safe_read () from /usr/lib/x86_64-linux-gnu/libmysqlclient.so.18
No symbol table info available.
#23 0x00007f8de589ee92 in ?? () from /usr/lib/x86_64-linux-gnu/libmysqlclient.so.18
No symbol table info available.
#24 0x00007f8de589fc5e in mysql_real_query () from /usr/lib/x86_64-linux-gnu/libmysqlclient.so.18
No symbol table info available.
#25 0x00007f8de565e07b in zif_mysqli_query () from /usr/lib/php5/20121212/mysqli.so
No symbol table info available.
#26 0x00007f8df19e832b in dtrace_execute_internal () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#27 0x00007f8df1aa8395 in ?? () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#28 0x00007f8df1a220c8 in execute_ex () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#29 0x00007f8df19e8229 in dtrace_execute_ex () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#30 0x00007f8df1aa89e0 in ?? () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#31 0x00007f8df1a220c8 in execute_ex () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#32 0x00007f8df19e8229 in dtrace_execute_ex () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#33 0x00007f8df1aa89e0 in ?? () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#34 0x00007f8df1a220c8 in execute_ex () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#35 0x00007f8df19e8229 in dtrace_execute_ex () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#36 0x00007f8df1aa89e0 in ?? () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#37 0x00007f8df1a220c8 in execute_ex () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#38 0x00007f8df19e8229 in dtrace_execute_ex () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#39 0x00007f8df1aa89e0 in ?? () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#40 0x00007f8df1a220c8 in execute_ex () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#41 0x00007f8df19e8229 in dtrace_execute_ex () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#42 0x00007f8df1aa89e0 in ?? () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#43 0x00007f8df1a220c8 in execute_ex () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#44 0x00007f8df19e8229 in dtrace_execute_ex () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#45 0x00007f8df1aa89e0 in ?? () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#46 0x00007f8df1a220c8 in execute_ex () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#47 0x00007f8df19e8229 in dtrace_execute_ex () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#48 0x00007f8df1aa89e0 in ?? () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#49 0x00007f8df1a220c8 in execute_ex () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#50 0x00007f8df19e8229 in dtrace_execute_ex () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#51 0x00007f8df19f9cb0 in zend_execute_scripts () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#52 0x00007f8df1999ae5 in php_execute_script () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#53 0x00007f8df1aaa032 in ?? () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#54 0x00007f8df5f8ebe0 in ap_run_handler ()
No symbol table info available.
#55 0x00007f8df5f8f129 in ap_invoke_handler ()
No symbol table info available.
#56 0x00007f8df5fa46ca in ap_process_async_request ()
No symbol table info available.
#57 0x00007f8df5fa49a4 in ap_process_request ()
No symbol table info available.
#58 0x00007f8df5fa1442 in ?? ()
No symbol table info available.
#59 0x00007f8df5f98220 in ap_run_process_connection ()
No symbol table info available.
#60 0x00007f8df23c9767 in ?? () from /usr/lib/apache2/modules/mod_mpm_prefork.so
No symbol table info available.
#61 0x00007f8df23c99a6 in ?? () from /usr/lib/apache2/modules/mod_mpm_prefork.so
No symbol table info available.
#50 0x00007f8df19e8229 in dtrace_execute_ex () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#51 0x00007f8df19f9cb0 in zend_execute_scripts () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#52 0x00007f8df1999ae5 in php_execute_script () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#53 0x00007f8df1aaa032 in ?? () from /usr/lib/apache2/modules/libphp5.so
No symbol table info available.
#54 0x00007f8df5f8ebe0 in ap_run_handler ()
No symbol table info available.
#55 0x00007f8df5f8f129 in ap_invoke_handler ()
No symbol table info available.
#56 0x00007f8df5fa46ca in ap_process_async_request ()
No symbol table info available.
#57 0x00007f8df5fa49a4 in ap_process_request ()
No symbol table info available.
#58 0x00007f8df5fa1442 in ?? ()
No symbol table info available.
#59 0x00007f8df5f98220 in ap_run_process_connection ()
No symbol table info available.
#60 0x00007f8df23c9767 in ?? () from /usr/lib/apache2/modules/mod_mpm_prefork.so
No symbol table info available.
#61 0x00007f8df23c99a6 in ?? () from /usr/lib/apache2/modules/mod_mpm_prefork.so
No symbol table info available.
#62 0x00007f8df23ca60e in ?? () from /usr/lib/apache2/modules/mod_mpm_prefork.so
No symbol table info available.
#63 0x00007f8df5f758ae in ap_run_mpm ()
No symbol table info available.
#64 0x00007f8df5f6f046 in main ()
No symbol table info available.

```

so what does that mean ... any idees what might be causing the segmentation fault? 
Or any ideas how to debug it?

---

### Post by matt_symes on 2016-02-06
Hi

Well it looks to be zend that's going bang so the problem is with PHP somewhere.

What php are you running ?

What php modules do you have installed ? Have you installed any extra php modules ?

> #17 <signal handler called>

Any idea what signal apache receives  ?

From the stack trace, it almost looks like apache is shutting down (maybe to restart) ?

Is this happening after an update ? 

> I often receive Apache segmentation faults.

You need to quantify this. When is it crashing ? Can you correlate these dates with any events in the log files ? 

Your best bet may be to generate a bug report and get the devs who know the code to look at it.

Kind regards

---

### Post by GZW on 2016-02-07
It crashes 1 - 3 times a week.
When it occurs for the first time, then it happens very often after. e.g.
```

[Wed Feb 03 15:19:22.946560 2016] [core:notice] [pid 4383] AH00051: child pid 16220 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Wed Feb 03 15:19:22.982508 2016] [core:notice] [pid 4383] AH00051: child pid 16401 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Wed Feb 03 15:19:22.982526 2016] [core:notice] [pid 4383] AH00051: child pid 16428 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Wed Feb 03 15:19:22.982536 2016] [core:notice] [pid 4383] AH00051: child pid 16438 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Wed Feb 03 15:19:25.985968 2016] [core:notice] [pid 4383] AH00051: child pid 16416 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Wed Feb 03 15:19:38.002097 2016] [core:notice] [pid 4383] AH00051: child pid 16411 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Wed Feb 03 15:19:38.002130 2016] [core:notice] [pid 4383] AH00051: child pid 16480 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Wed Feb 03 15:19:39.003304 2016] [core:notice] [pid 4383] AH00051: child pid 16393 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Wed Feb 03 15:19:39.003325 2016] [core:notice] [pid 4383] AH00051: child pid 16425 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Wed Feb 03 15:19:40.005402 2016] [core:notice] [pid 4383] AH00051: child pid 16279 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Wed Feb 03 15:19:40.005449 2016] [core:notice] [pid 4383] AH00051: child pid 16319 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Wed Feb 03 15:19:40.005471 2016] [core:notice] [pid 4383] AH00051: child pid 16458 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Wed Feb 03 15:19:41.009061 2016] [core:notice] [pid 4383] AH00051: child pid 16478 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Wed Feb 03 15:19:42.015744 2016] [core:notice] [pid 4383] AH00051: child pid 16376 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Wed Feb 03 15:19:42.015803 2016] [core:notice] [pid 4383] AH00051: child pid 16448 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Wed Feb 03 15:19:43.016946 2016] [core:notice] [pid 4383] AH00051: child pid 16368 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Wed Feb 03 15:19:44.019400 2016] [core:notice] [pid 4383] AH00051: child pid 16432 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Wed Feb 03 15:19:45.020544 2016] [core:notice] [pid 4383] AH00051: child pid 16406 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Wed Feb 03 15:19:46.021617 2016] [core:notice] [pid 4383] AH00051: child pid 16400 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Wed Feb 03 15:19:47.023989 2016] [core:notice] [pid 4383] AH00051: child pid 16422 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Wed Feb 03 15:19:47.024039 2016] [core:notice] [pid 4383] AH00051: child pid 16479 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Wed Feb 03 15:19:48.027294 2016] [core:notice] [pid 4383] AH00051: child pid 16333 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Wed Feb 03 15:19:50.034057 2016] [core:notice] [pid 4383] AH00051: child pid 16495 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Wed Feb 03 15:19:51.034589 2016] [core:notice] [pid 4383] AH00051: child pid 16114 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Wed Feb 03 15:19:51.034648 2016] [core:notice] [pid 4383] AH00051: child pid 16477 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Wed Feb 03 15:19:52.036936 2016] [core:notice] [pid 4383] AH00051: child pid 16394 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Wed Feb 03 15:19:52.036994 2016] [core:notice] [pid 4383] AH00051: child pid 16513 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Wed Feb 03 15:19:53.040286 2016] [core:notice] [pid 4383] AH00051: child pid 16315 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Wed Feb 03 15:19:55.044063 2016] [core:notice] [pid 4383] AH00051: child pid 16461 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Wed Feb 03 15:19:57.048169 2016] [core:notice] [pid 4383] AH00051: child pid 16527 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Wed Feb 03 15:19:58.049342 2016] [core:notice] [pid 4383] AH00051: child pid 16353 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Wed Feb 03 15:19:59.050510 2016] [core:notice] [pid 4383] AH00051: child pid 16542 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Wed Feb 03 15:20:00.051714 2016] [core:notice] [pid 4383] AH00051: child pid 16335 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Wed Feb 03 15:20:01.054176 2016] [core:notice] [pid 4383] AH00051: child pid 16506 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Wed Feb 03 15:20:02.057471 2016] [core:notice] [pid 4383] AH00051: child pid 16348 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump
[Wed Feb 03 15:20:04.060897 2016] [core:notice] [pid 4383] AH00051: child pid 16581 exit signal Segmentation fault (11), possible coredump in /tmp/apache2-gdb-dump

```
... and so on.

Then the users receive a 500(?) server error. The webpages are not loaded anymore. I need to restart Apache.

When it occurs, there are no Server updates installed.

I attach my phpinfo() - maybe you have any ideas?

I suppose there is somewhere a PHP error, maybe a coding error by our devs, but I don't know how to locate it. We have a lot of coding. No information in my PHP error file when it occurs.

edit: I am not a Server expert, I am a PHP developer, I know most parts of our code.

---

### Post by matt_symes on 2016-02-07
Hi

For some background...

Are you using any PHP framework such as drupal ?

Is apache running on bare metal, a VM or a container ?

Kind regards

---

### Post by GZW on 2016-03-04
Fortunately, the last Ubuntu Apache update did seem to solve the issue. I installed the latest patches 3 weeks ago, since then, no more dumps occured. *puh*

---

