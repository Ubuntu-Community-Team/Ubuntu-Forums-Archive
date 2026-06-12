---
title: "Munin and Apache problem"
date: 2009-05-26
forum: Server Platforms
---

### Post by LepeKaname on 2009-05-26
Hi, and thank you in advance...

I Installed munin and I'm monitoring 4 servers (The setup is pretended to be exactly the same... ). I don't have any problem except in one:

Apache processes are not shown (means, the option for "Apache" is not there. 

I tried directly in /usr/share/munin/plugins/

```
./apache_processes autoconf
```

and the answer is "yes".

the same for apache_accesses

If I try: [http://localhost/server-status?auto](http://localhost/server-status?auto)
I receive:
```
Total Accesses: 896
Total kBytes: 5570
CPULoad: .00853268
Uptime: 6563
ReqPerSec: .0146275
BytesPerSec: 86.9066
BytesPerReq: 5941.33
BusyWorkers: 1
IdleWorkers: 8
Scoreboard: ____W____.......................................................................................................................................................................................................................................................

```
So I feel my Apache configuration is correct...right?

I restarted munin-node and I even remove everything from /var/www/munin/ directory. But when it is generated still I don't see any file with "apache" in there...

Any idea?

---

### Post by ian dobson on 2009-05-27
Hi,

What do you see when you try 

munin-run apache_processes config

and 
munin-run apache_processes

Regards
Ian Dobson

---

### Post by LepeKaname on 2009-05-27
Hi Ian, 

This is what I get:

> $ munin-run apache_processes config
ERROR: Could not execute plugin (plugin doesn't exist?).

$ munin-run apache_processes       
ERROR: Could not execute plugin (plugin doesn't exist?).

$ munin-run apache_accesses 
ERROR: Could not execute plugin (plugin doesn't exist?).

/usr/share/munin/plugins$ ls -l
total 500
-rwxr-xr-x 1 root root  1594 May 10  2008 acpi
-rwxr-xr-x 1 root root  3999 May 10  2008 apache_accesses
-rwxr-xr-x 1 root root  4090 May 10  2008 apache_processes
-rwxr-xr-x 1 root root  4001 May 10  2008 apache_volume
...

I tried the same in the other server (where it is working) and Its fine:

> $ munin-run apache_processes
busy80.value 1
idle80.value 9

But not for accesses:
> 
$ munin-run apache_accesses
ERROR: Could not execute plugin (plugin doesn't exist?).

What is wrong?

This is my munin.conf (without comments):

> dbdir   /var/lib/munin
htmldir /var/www/munin
logdir  /var/log/munin
rundir  /var/run/munin

tmpldir /etc/munin/templates

[localhost.localdomain]
    address 127.0.0.1
    use_node_name yes

Thank you.

---

### Post by LepeKaname on 2009-05-27
I think you point me in the right direction...

I found that in /etc/munin/plugins/ apache_processes was missing in that specific server... Its strange since apache was installed (and running) before munin... But anyway... I also added the link to apache processes and restarted munin-node. 
Just a sec ago, I saw the changes... we can close this issue.. thank you a lot!

---

### Post by ian dobson on 2009-05-27
Hi,

Normally the plugins are stored in /usr/share/munin/plugins and a symbolic link from /etc/munin/plugins to the required plugin in the /usr directory.

PS. Waiting only one day for someone to answer your questions is asking abit much, it could take afew days for someone to see your post and know where the problem is.

Regards
Ian Dobson

---

