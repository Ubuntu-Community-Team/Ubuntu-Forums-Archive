---
title: "ufw.log missing?"
date: 2017-12-16
forum: Security
---

### Post by g3kxyz on 2017-12-16
I've installed ufw on 4 servers now but only one of them has the file ufw.log under /var/log

I can't figure out where the ufw logs are going on. I'm not seeing them logged anywhere.

If i check with ufw status verbose it tells me it is logging but where??

Status: active
Logging: on (low)

---

### Post by g3kxyz on 2017-12-27
wow. I guess I expected some help but this forum must be dead enough to not offer any. Guess I'll have to find another Linux forum to ask my question on.

---

### Post by QIII on 2017-12-27
Or ... you could bump your thread instead of letting it sink to the bottom.  If you have no response in 12 hours, simply add a new post with the word "bump".

---

### Post by #&amp;thj^% on 2017-12-27
There is just not a lot of information to help you here.
For example is this enabled:
```
sudo ufw logging on
Logging enabled

```
As much information you can provide will attract more volunteers. :D
And you said that you looked here:
```
sudo ls /var/log/ufw*
```

---

### Post by g3kxyz on 2017-12-27
Yes logging is enabled. Yes there is no ufw.log file or anything called ufw at all anywhere under /var/log

```
root@apollo:/var/log# ufw logging on
Logging enabled
root@apollo:/var/log# ls /var/log/ufw*
ls: cannot access '/var/log/ufw*': No such file or directory
```

I don't understand why it wouldn't create a ufw.log file when ufw is enabled and it is actively blocking connections

---

### Post by #&amp;thj^% on 2017-12-27
Humm? what dose this show then:
```
nano /var/log/gufw.log
```
Mine Reports:
```
[11/30/2017 06:23:22 PM] Status: Enabled

```
This may get a bit tedious but hang in here.

---

### Post by g3kxyz on 2017-12-27
if I type in 
```
[COLOR=#000000][FONT=&quot]nano /var/log/gufw.log[/FONT][/COLOR]
```
then it just tries to create a brand new empty file as if it doesn't exist at all.

---

### Post by g3kxyz on 2017-12-27
I only see the following under /var/log

```
root@apollo:/var/log# ls
alternatives.log  apt       btmp             dmesg     faillog         fsck     mail.log  php7.0-fpm.log  syslog      wtmp
apache2           auth.log  dbconfig-common  dpkg.log  fontconfig.log  lastlog  mysql     samba           vsftpd.log
```

Even if I try to view hidden logs. same result
```
root@apollo:/var/log# ls -a
.   alternatives.log  apt       btmp             dmesg     faillog         fsck     mail.log  php7.0-fpm.log  syslog      wtmp
..  apache2           auth.log  dbconfig-common  dpkg.log  fontconfig.log  lastlog  mysql     samba           vsftpd.log
```

---

### Post by #&amp;thj^% on 2017-12-27
> **g3kxyz said:**
> if I type in 
```
[COLOR=#000000][FONT=&quot]nano /var/log/gufw.log[/FONT][/COLOR]
```
then it just tries to create a brand new empty file as if it doesn't exist at all.

that's a good point to a problem then.
See if anything is here then and paste back:
```
nano /etc/rsyslog.d/20-ufw.conf 
```

---

### Post by g3kxyz on 2017-12-27
I see the following in [COLOR=#000000][FONT=&quot]nano /etc/rsyslog.d/20-ufw.conf[/FONT][/COLOR]

```
# Log kernel generated UFW log messages to file
:msg,contains,"[UFW " /var/log/ufw.log


# Uncomment the following to stop logging anything that matches the last rule.
# Doing this will stop logging kernel generated UFW log messages to the file
# normally containing kern.* messages (eg, /var/log/kern.log)
#& stop

```

---

### Post by #&amp;thj^% on 2017-12-27
> **g3kxyz said:**
> I see the following in [COLOR=#000000][FONT=&quot]nano /etc/rsyslog.d/20-ufw.conf[/FONT][/COLOR]

```
# Log kernel generated UFW log messages to file
:msg,contains,"[UFW " /var/log/ufw.log


# Uncomment the following to stop logging anything that matches the last rule.
# Doing this will stop logging kernel generated UFW log messages to the file
# normally containing kern.* messages (eg, /var/log/kern.log)
#& stop

```
Ok Great try with this then add to the bottom:

```
tail -1 /etc/rsyslog.d/20-ufw.conf 
& stop

```
Then restart rsyslog:
```
sudo systemctl restart rsyslog
```
And now they should be in /var/log/ufw.log and not in /var/log/syslog anymore

---

### Post by g3kxyz on 2017-12-27
Added it exactly as you said

[COLOR=#000000]*nano /etc/rsyslog.d/20-ufw.conf*[/COLOR]

```
# Log kernel generated UFW log messages to file:msg,contains,"[UFW " /var/log/ufw.log


# Uncomment the following to stop logging anything that matches the last rule.
# Doing this will stop logging kernel generated UFW log messages to the file
# normally containing kern.* messages (eg, /var/log/kern.log)
#& stop


$ tail -1 /etc/rsyslog.d/20-ufw.conf
& stop
```

restarted with
```
[COLOR=#000000][FONT=&amp]sudo systemctl restart rsyslog[/FONT][/COLOR]
```

but now I see this in /var/log/syslog
```

Dec 27 15:18:20 apollo systemd[1]: Starting System Logging Service...
Dec 27 15:18:20 apollo rsyslogd-2039: Could not open output pipe '/dev/xconsole':: No such file or directory [v8.16.0 try http://www.rsyslog.com/e/2039 ]
Dec 27 15:18:20 apollo systemd[1]: Started System Logging Service.
Dec 27 15:18:20 apollo rsyslogd-2007: action 'action 11' suspended, next retry is Wed Dec 27 15:18:50 2017 [v8.16.0 try http://www.rsyslog.com/e/2007 ]
Dec 27 15:18:20 apollo rsyslogd-3003: invalid or yet-unknown config file command 'KLogPermitNonKernelFacility' - have you forgotten to load a module? [v8.16.0 try http://www.rsyslog.com/e/3003 ]
Dec 27 15:18:20 apollo rsyslogd-2207: error during parsing file /etc/rsyslog.d/20-ufw.conf, on or before line 9: invalid character '$' - is there an invalid escape sequence somewhere? [v8.16.0 try http://www.rsyslog.com/e/2207 ]
Dec 27 15:18:20 apollo rsyslogd-2184: action 'tail' treated as ':omusrmsg:tail' - please use ':omusrmsg:tail' syntax instead, 'tail' will not be supported in the future [v8.16.0 try http://www.rsyslog.com/e/2184 ]
Dec 27 15:18:20 apollo rsyslogd-2207: error during parsing file /etc/rsyslog.d/20-ufw.conf, on or before line 9: warnings occured in file '/etc/rsyslog.d/20-ufw.conf' around line 9 [v8.16.0 try http://www.rsyslog.com/e/2207 ]
Dec 27 15:18:20 apollo rsyslogd-2207: error during parsing file /etc/rsyslog.d/20-ufw.conf, on or before line 9: errors occured in file '/etc/rsyslog.d/20-ufw.conf' around line 9 [v8.16.0 try http://www.rsyslog.com/e/2207 ]
Dec 27 15:18:20 apollo rsyslogd: rsyslogd's groupid changed to 111
Dec 27 15:18:20 apollo rsyslogd: rsyslogd's userid changed to 106
Dec 27 15:18:38 apollo rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="4719" x-info="http://www.rsyslog.com"] exiting on signal 15.
Dec 27 15:18:38 apollo rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="4726" x-info="http://www.rsyslog.com"] start
Dec 27 15:18:38 apollo rsyslogd-3003: invalid or yet-unknown config file command 'KLogPermitNonKernelFacility' - have you forgotten to load a module? [v8.16.0 try http://www.rsyslog.com/e/3003 ]
Dec 27 15:18:38 apollo rsyslogd-2207: error during parsing file /etc/rsyslog.d/20-ufw.conf, on or before line 9: invalid character '$' - is there an invalid escape sequence somewhere? [v8.16.0 try http://www.rsyslog.com/e/2207 ]
Dec 27 15:18:38 apollo rsyslogd-2184: action 'tail' treated as ':omusrmsg:tail' - please use ':omusrmsg:tail' syntax instead, 'tail' will not be supported in the future [v8.16.0 try http://www.rsyslog.com/e/2184 ]
Dec 27 15:18:38 apollo rsyslogd-2207: error during parsing file /etc/rsyslog.d/20-ufw.conf, on or before line 9: warnings occured in file '/etc/rsyslog.d/20-ufw.conf' around line 9 [v8.16.0 try http://www.rsyslog.com/e/2207 ]
Dec 27 15:18:38 apollo rsyslogd-2207: error during parsing file /etc/rsyslog.d/20-ufw.conf, on or before line 9: errors occured in file '/etc/rsyslog.d/20-ufw.conf' around line 9 [v8.16.0 try http://www.rsyslog.com/e/2207 ]
Dec 27 15:18:38 apollo rsyslogd: rsyslogd's groupid changed to 111
Dec 27 15:18:38 apollo rsyslogd: rsyslogd's userid changed to 106

```

if I do this at term # /var/log# grep ufw syslog

it gives me this below
```
Dec 26 19:40:25 apollo ufw-init[52]: modprobe: ERROR: ../libkmod/libkmod.c:586 kmod_search_moddep() could not open moddep file '/lib/modules/2.6.32-042stab126.1/modules.dep.bin'
Dec 26 19:40:25 apollo ufw-init[52]: modprobe: FATAL: Module nf_conntrack_ftp not found in directory /lib/modules/2.6.32-042stab126.1
Dec 26 19:40:25 apollo ufw-init[52]: modprobe: ERROR: ../libkmod/libkmod.c:586 kmod_search_moddep() could not open moddep file '/lib/modules/2.6.32-042stab126.1/modules.dep.bin'
Dec 26 19:40:25 apollo ufw-init[52]: modprobe: FATAL: Module nf_nat_ftp not found in directory /lib/modules/2.6.32-042stab126.1
Dec 26 19:40:25 apollo ufw-init[52]: modprobe: ERROR: ../libkmod/libkmod.c:586 kmod_search_moddep() could not open moddep file '/lib/modules/2.6.32-042stab126.1/modules.dep.bin'
Dec 26 19:40:25 apollo ufw-init[52]: modprobe: FATAL: Module nf_conntrack_netbios_ns not found in directory /lib/modules/2.6.32-042stab126.1
Dec 26 19:40:25 apollo ufw-init[52]: sysctl: permission denied on key 'net.ipv4.tcp_sack'
Dec 27 15:18:20 apollo rsyslogd-2207: error during parsing file /etc/rsyslog.d/20-ufw.conf, on or before line 9: invalid character '$' - is there an invalid escape sequence somewhere? [v8.16.0 try http://www.rsyslog.com/e/2207 ]
Dec 27 15:18:20 apollo rsyslogd-2207: error during parsing file /etc/rsyslog.d/20-ufw.conf, on or before line 9: warnings occured in file '/etc/rsyslog.d/20-ufw.conf' around line 9 [v8.16.0 try http://www.rsyslog.com/e/2207 ]
Dec 27 15:18:20 apollo rsyslogd-2207: error during parsing file /etc/rsyslog.d/20-ufw.conf, on or before line 9: errors occured in file '/etc/rsyslog.d/20-ufw.conf' around line 9 [v8.16.0 try http://www.rsyslog.com/e/2207 ]
Dec 27 15:18:38 apollo rsyslogd-2207: error during parsing file /etc/rsyslog.d/20-ufw.conf, on or before line 9: invalid character '$' - is there an invalid escape sequence somewhere? [v8.16.0 try http://www.rsyslog.com/e/2207 ]
Dec 27 15:18:38 apollo rsyslogd-2207: error during parsing file /etc/rsyslog.d/20-ufw.conf, on or before line 9: warnings occured in file '/etc/rsyslog.d/20-ufw.conf' around line 9 [v8.16.0 try http://www.rsyslog.com/e/2207 ]
Dec 27 15:18:38 apollo rsyslogd-2207: error during parsing file /etc/rsyslog.d/20-ufw.conf, on or before line 9: errors occured in file '/etc/rsyslog.d/20-ufw.conf' around line 9 [v8.16.0 try http://www.rsyslog.com/e/2207 ]
Dec 27 15:23:10 apollo rsyslogd-2207: error during parsing file /etc/rsyslog.d/20-ufw.conf, on or before line 9: warnings occured in file '/etc/rsyslog.d/20-ufw.conf' around line 9 [v8.16.0 try http://www.rsyslog.com/e/2207 ]
Dec 27 15:23:10 apollo rsyslogd-2207: error during parsing file /etc/rsyslog.d/20-ufw.conf, on or before line 9: errors occured in file '/etc/rsyslog.d/20-ufw.conf' around line 9 [v8.16.0 try http://www.rsyslog.com/e/2207 ]

```

---

### Post by g3kxyz on 2017-12-27
Something tells me it hasn't been logging [UFW in the /var/log/syslog file either because I can't find any traces of it there.

---

### Post by g3kxyz on 2017-12-27
I found the [UFW BLOCK] logs by typing dmesg in terminal so for some reason they are logging to dmesg instead.

I'm not exactly sure how to change this logging behavior.

---

### Post by #&amp;thj^% on 2017-12-27
Something is syntactically wrong with the mentioned config file, so that further interpretation is impossible. The error most often actually is on the quoted line, or at least very close in front of it. A syntax error can be caused by invalid spelling of RainerScript commands, e.g. "stopp" instead of the correct "stop". 
But yours looks good from here?
Hope you kept that terminal open lets try this instead then remove those 2 lines and instead add this** to the Top this time**:
```
:msg, contains, "UFW" -/var/log/ufw.log
& ~

```
you already have this ":msg,contains,"[UFW " /var/log/ufw.log"
Just a:
```
& ~
```
Save and restart:
```
sudo systemctl restart rsyslog
```
Now look at  all data that contains "UFW" in /var/log/ufw.log

---

### Post by QIII on 2017-12-27
I think the issue is here:

```
Dec 27 15:18:38 apollo rsyslogd-2207: error during parsing file /etc/rsyslog.d/20-ufw.conf, on or before line 9: invalid character '$' - is there an invalid escape sequence somewhere? [v8.16.0 try http://www.rsyslog.com/e/2207 ]

```

Try replacing

```
$ tail -1 /etc/rsyslog.d/20-ufw.conf
```

in 20-ufw.conf with

```
tail -1 /etc/rsyslog.d/20-ufw.conf
```

Let us know if that helps.

---

### Post by g3kxyz on 2017-12-27
Now the file looks like this

```
# Log kernel generated UFW log messages to file:msg,contains,"[UFW " /var/log/ufw.log
& ~


# Uncomment the following to stop logging anything that matches the last rule.
# Doing this will stop logging kernel generated UFW log messages to the file
# normally containing kern.* messages (eg, /var/log/kern.log)
#:msg, contains, "UFW" -/var/log/ufw.log


#& stop
```

restarted rsyslog

No change in /var/log
```
root@apollo:/var/log# ls
alternatives.log  apt       btmp             dmesg     faillog         fsck     mail.log  php7.0-fpm.log  syslog      wtmp
apache2           auth.log  dbconfig-common  dpkg.log  fontconfig.log  lastlog  mysql     samba           vsftpd.log
```

Still see a ton of  [UFW BLOCK] in dmesg. My guess is iptables is doing the logging.

---

### Post by #&amp;thj^% on 2017-12-27
> **QIII said:**
> I think the issue is here:

```
Dec 27 15:18:38 apollo rsyslogd-2207: error during parsing file /etc/rsyslog.d/20-ufw.conf, on or before line 9: invalid character '$' - is there an invalid escape sequence somewhere? [v8.16.0 try http://www.rsyslog.com/e/2207 ]

```

Try replacing

```
$ tail -1 /etc/rsyslog.d/20-ufw.conf
```

in 20-ufw.conf with

```
tail -1 /etc/rsyslog.d/20-ufw.conf
```

Let us know if that helps.
Good Spot QIII +1
I tell ya I'm going Blind...LOL

> **g3kxyz said:**
> Now the file looks like this

```
# Log kernel generated UFW log messages to file:msg,contains,"[UFW " /var/log/ufw.log
& ~


# Uncomment the following to stop logging anything that matches the last rule.
# Doing this will stop logging kernel generated UFW log messages to the file
# normally containing kern.* messages (eg, /var/log/kern.log)
#:msg, contains, "UFW" -/var/log/ufw.log


#& stop
```

restarted rsyslog

No change in /var/log
```
root@apollo:/var/log# ls
alternatives.log  apt       btmp             dmesg     faillog         fsck     mail.log  php7.0-fpm.log  syslog      wtmp
apache2           auth.log  dbconfig-common  dpkg.log  fontconfig.log  lastlog  mysql     samba           vsftpd.log
```

Still see a ton of  [UFW BLOCK] in dmesg. My guess is iptables is doing the logging.
Yep that to be expected wrong syntax should look like this:
```
:msg, contains, "UFW" -/var/log/ufw.log
& ~
```
But try with the new syntax QIII picked out!

---

### Post by g3kxyz on 2017-12-27
right now 20-ufw.conf contains the following

```

# Log kernel generated UFW log messages to file
:msg,contains,"[UFW " /var/log/ufw.log


# Uncomment the following to stop logging anything that matches the last rule.
# Doing this will stop logging kernel generated UFW log messages to the file
# normally containing kern.* messages (eg, /var/log/kern.log)


tail -1 /etc/rsyslog.d/20-ufw.conf
& stop

```

is that what u want me to try?

---

### Post by #&amp;thj^% on 2017-12-27
Yes Please.

---

### Post by g3kxyz on 2017-12-27
ok no major errors in syslog
```

Dec 27 16:08:40 apollo systemd[1]: Stopped System Logging Service.
Dec 27 16:08:40 apollo systemd[1]: Starting System Logging Service...
Dec 27 16:08:40 apollo systemd[1]: Started System Logging Service.


```

but there is no ufw.log file either. after restarting rsyslog

```
root@apollo:/var/log# ls -a
.   alternatives.log  apt       btmp             dmesg     faillog         fsck     mail.log  php7.0-fpm.log  syslog      wtmp
..  apache2           auth.log  dbconfig-common  dpkg.log  fontconfig.log  lastlog  mysql     samba           vsftpd.log

```

Still see the UFW logs in dmesg which I guess is normal but annoying that they only exist there.

---

### Post by g3kxyz on 2017-12-27
on my other server where UFW.log does exist

```
root@g3k:/var/log# ls
alternatives.log       apt            btmp             dpkg.log.2.gz      installer      letsencrypt    mail.log.3.gz  syslog.2.gz  ufw.log.1            vsftpd.log.2
alternatives.log.1     auth.log       btmp.1           dpkg.log.3.gz      kern.log       lxd            mail.log.4.gz  syslog.3.gz  ufw.log.2.gz         vsftpd.log.3
alternatives.log.2.gz  auth.log.1     dbconfig-common  fail2ban.log       kern.log.1     mail.err       mysql          syslog.4.gz  ufw.log.3.gz         vsftpd.log.4
alternatives.log.3.gz  auth.log.2.gz  dist-upgrade     fail2ban.log.1     kern.log.2.gz  mail.err.1     owncloud.log   syslog.5.gz  ufw.log.4.gz         wtmp
apache2                auth.log.3.gz  dmesg            fail2ban.log.2.gz  kern.log.3.gz  mail.log       samba          syslog.6.gz  unattended-upgrades  wtmp.1
apport.log             auth.log.4.gz  dpkg.log         faillog            kern.log.4.gz  mail.log.1     syslog         syslog.7.gz  vsftpd.log
apport.log.1           bootstrap.log  dpkg.log.1       fsck               lastlog        mail.log.2.gz  syslog.1       ufw.log      vsftpd.log.1
```

the file "nano /etc/rsyslog.d/20-ufw.conf" looks like this
```
# Log kernel generated UFW log messages to file
:msg,contains,"[UFW " /var/log/ufw.log


# Uncomment the following to stop logging anything that matches the last rule.
# Doing this will stop logging kernel generated UFW log messages to the file
# normally containing kern.* messages (eg, /var/log/kern.log)
#& stop
```

This is pretty frustrating. Only thing different about the two servers is g3k is a physical linux box and the 4 servers where ufw.log isn't working are VPS servers.

---

### Post by #&amp;thj^% on 2017-12-27
Wait a bit and if you still don't see any post back.
But that all looks good to me anyway.

---

### Post by QIII on 2017-12-27
> **g3kxyz said:**
> Only thing different about the two servers is g3k is a physical linux box and the 4 servers where ufw.log isn't working are VPS servers.

That's an interesting tidbit...

Does your VPS provider provision your servers or did you install them?

---

### Post by g3kxyz on 2017-12-27
> **QIII said:**
> That's an interesting tidbit...

Does your VPS provider provision your servers or did you install them?

They provision them. I had to pick from a list of distros and then was able to install from a control panel but that's all the control I had over the install of the OS install. They were installed with Ubuntu 16.04 minimal same as my server "g3k".

---

### Post by g3kxyz on 2017-12-27
> **1fallen said:**
> Wait a bit and if you still don't see any post back.
But that all looks good to me anyway.

Not sure how long I should wait but there are new [UFW BLOCK] messages in dmesg, one of which I created on purpose from our 2nd ISP backbone to see if it would generate the ufw.log file. 

So far no file exists under /var/log

I tested with another linux server in house and enabled ufw, I disobeyed the firewall rule on purpose and poof ufw.log was created instantly.

---

### Post by QIII on 2017-12-27
This might be something to talk to your VPS provider about while you wait to see if the community here can figure something out.  It would be great to learn if this is something other users might benefit from.

---

### Post by #&amp;thj^% on 2017-12-27
I'm kind of stumped here??
We can make sure that ufw is running on the faulty machines with:
```
systemctl enable ufw.service
```
And:
```
systemctl start ufw.service
```
Checking again with:
```
sudo ufw status verbose
```
Mine will differ from yours:
```
sudo ufw status verbose
Status: active
Logging: on (high)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip

```

**EDIT:**
I have done some investigation into this issue.
I don't believe there is a way around this.
The dmesg command directly prints the contents of the Kernel Ring Buffer. This contains all the ufw log entries that you are seeing.
The **/etc/rsyslog.d/20-ufw.conf** file is telling rsyslog which of the ufw entries in the Kernel Ring Buffer to log to either the** /var/log/ufw.log** or **/var/log/kern.log.**
You can prevent the ufw entries from being logged to /var/log/kern.log (to remove duplication) by uncommenting the line in **/etc/rsyslog.d/20-ufw.conf** that contains **"& ~"**.

Unfortunately there is no way to prevent the dmesg command from displaying these messages.

---

### Post by QIII on 2017-12-27
There's an additional wrinkle here in that the VPS provider can make slight modifications to the behavior of the OS in their provision.  They do this to avoid complications on their physical machines.  For instance, memory management is often locked down because the physical memory is shared between a number of virtual machines.

In this case, the VPS provider may have restricted some portion of logging to avoid a conflict with the performance of other clients' VMs.

Some firewall provisions may be restricted to avoid any client machine from being compromised and risking a chain reaction of compromise across all guests on the physical machine.

---

