---
title: "Apache2 restart kills mod-mono"
date: 2009-01-16
forum: Server Platforms
---

### Post by grognut on 2009-01-16
Hi all,

I've got mod_mono running on Hardy by copiling from source using this guide:
[HTML]http://studentguru.gr/blogs/kingherc/archive/2008/05.aspx[/HTML]

It allows php and mod_mono to run.
I downloaded the latest versions from the mono web site and it works!! BUT
If I restart apache using  

```
root@x:~# /etc/init.d/apache2 restart
```

I get
```

 * Restarting web server apache2
[Fri Jan 16 23:48:02 2009] [crit] (13)Permission denied: Failed to attach to existing dashboard, and removing dashboard file '/tmp/mod_mono_dashboard_XXGLOBAL_1' failed (Operation not permitted). Further action impossible.                                                                 [ OK ]
```
and from the log file 
```
[Fri Jan 16 23:52:22 2009] [warn] (2)No such file or directory: Failed to destroy the '/tmp/mod_mono_dashboard_XXGLOBAL_1' shared memory dashboard
[Fri Jan 16 23:52:33 2009] [notice] Apache/2.2.8 (Ubuntu) mod_mono/2.0 PHP/5.2.4-2ubuntu5.4 with Suhosin-Patch configured -- resuming normal operations

```


This kills mod_mono so now aspx pages are not served but offered for download. 
I know this is not a Ubuntu packaged app but can anyone help. I've google for but I can't find a solution.

I do find that if I reboot the system it will work. 
If I stop apache the file is not there. If I start apache it appears.

Can anyone help.

I know the obvious answer is not to restart apache but I'm modding the config file regularly at the moment.
I havent tried a reload yet.
Cheers
grognut

---

### Post by grognut on 2009-01-23
I found a solution.
I removed the compiled code and used badgerports.

This still gave the problem of 

```
 * Restarting web server apache2
[Fri Jan 16 23:48:02 2009] [crit] (13)Permission denied: Failed to attach to existing dashboard, and removing dashboard file '/tmp/mod_mono_dashboard_XXGLOBAL_1' failed (Operation not permitted). Further action impossible.                                                                 [ OK ]
```

but I found that if you 
a2dismod mod_mono
/etc/init.d/apache2 restart
a2enmod mon_mono
/etc/init.d/apache2 restart

it starts OK without the error.

Still can't get mysql working though. I feel another thread coming on.

Cheers

Grognut

---

