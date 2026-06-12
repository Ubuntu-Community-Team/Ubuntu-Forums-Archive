---
title: "apache stops responding after a few days"
date: 2008-11-25
forum: Server Platforms
---

### Post by davidshere on 2008-11-25
I'm experiencing a memory problem with apache.  Apache stops responding to webpage requests after a few days.  When we first discovered this problem, there were 214 apache processes and all of the virtual memory was full.  

Steps I have taken:
1.  I reduced the MaxClients option to 25 (it was previously at 150) and rebooted the box.  This seems to effectively limit the number of apache processes, but the memory usage continued to rise and about 2 days later apache stopped responding again.  The swap memory was still at 0 but the physical memory was at about 440MB.
2.  I reduced the MaxRequestsPerChild to 40 (it was previously unlimited).  This appears to make no difference at all; the same behavior we saw under Step #1 is still there.  It's been running like this for only about an hour and the memory usage has gone from ~113MB at startup to ~300MB now.

In each case the average apache process is about 18MB, which is similar to apache installations I have running on other machines.  When apache stops responding, restarting apache will get apache to start responding again, but none of the child processes running before the restart are killed.  The only way to free up the memory and stop these processes is to reboot the machine.   Right now our workaround is to reboot the machine daily.

I'm running server 8.04 on a virtual machine, with apache2, mysql5, and php5.  All up to date.  The machine has 512 MB RAM.  We host about 8 websites on this server and it gets light to moderate traffic.  Most sites are mambo or some equivalent CMS.  All work fine for a few days after the machine is started.  These sites and 3 others were previously on a FreeBSD machine and worked very well.

Possibilities I've considered:
1.  Limitations of virtual machine -- kernel issues causing memory leaks
2.  Something in one of the PHP CMSs is leaking memory -- unlikely since the sites worked fine on the FreeBSD machine.
3.  Something in the apache configuration still needs to be tweaked.
4.  Apache bug.

Any help or suggestions would be greatly appreciated.

---

### Post by Philio on 2008-11-25
Considering that you probably want a memory limit for Apache of no more than 250Mb if your VPS has 512Mb and that processes are using up to 18Mb you should probably consider lowering the MaxClients value a bit further.

250/18 = 13

If you don't have that much traffic maybe a setting of 10 will suffice here.

You should also take a look at the following:

StartServers
MinSpareServers
MaxSpareServers

They will probably be fine at their default settings of 5, 5 and 10 respectively, I assume the MaxClients value will override the MaxSpareServers value of 10 (or you could set it to 5).

If you think you may have memory leaks MaxRequestsPerChild with a non-zero value is a good idea. This setting means that Apache will kill off the child process after it processes MaxRequestsPerChild number of requests. I'm not sure what a good setting for this is, but I assume a lower setting will help to limit the memory usage for Apache over time.

---

### Post by Philio on 2008-11-25
A bit more to add...

The fact you had over 200 processes means 1 of 2 things really.

1. You have loads of requests coming into the server.
2. Your Apache processes are hanging for some reason, which could be (for example) related to scripts or a problem with the MySQL server as well as an Apache problem.

It's more than likely the 2nd option.

I would see if limiting Apache's memory usage as above works first and if you encounter the issue again try and check as many other processes on your server to see if the issue is limited purely to Apache. MySQL for example, login and check 'show processlist' from the command line.

---

### Post by davidshere on 2008-11-25
Thanks!  A couple questions:

> **Philio said:**
> 

You should also take a look at the following:

StartServers
MinSpareServers
MaxSpareServers

I have two sections that have these settings.  Should they match or does one not matter... ?

```
<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers       5
    MaxClients           10
    MaxRequestsPerChild   20
</IfModule>

```

and 

```
<IfModule mpm_worker_module>
    StartServers          2
    MaxClients           25
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadsPerChild      25
    MaxRequestsPerChild   40
</IfModule>
```

---

### Post by Philio on 2008-11-25
MPM worker is a threaded model.
MPM prefork is a forked model.

If that means nothing, your using PHP so you'll be using MPM prefork :)

You only need to change the settings for the MPM prefork section.

---

### Post by davidshere on 2008-11-26
Thanks very much for your suggestions... unfortunately the problem remains.  I might troubleshoot some more but for now I'm just going to reboot the box every night.

Lowering the processes/clients/memory just seems to reduce the amount of time it takes before apache stops responding...

EDIT:
I've changed the settings to this:```
<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers       6
    MaxClients            5
    MaxRequestsPerChild   5
</IfModule>

```

Which seems to have made things better.  It's actually killing apache processes, which it wasn't doing before.  I'll have to wait a few days to know for sure though.

---

