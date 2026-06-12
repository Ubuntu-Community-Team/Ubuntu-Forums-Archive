---
title: "hostname (none)"
date: 2010-12-08
forum: Server Platforms
---

### Post by cbob on 2010-12-08
Hello,

Just upgraded from Ubuntu Server 9.04 to 10.04 and in the process my hostname was lost.
```
[FONT=courier new]$ hostname[/FONT]
[FONT=courier new](none)[/FONT]
 
[FONT=courier new]$ uname -n[/FONT]
[FONT=courier new](none)[/FONT]
```Although configure file looks fine:
```
[FONT=courier new]$ cat /etc/hostname[/FONT]
[FONT=courier new]bob_ubuntu[/FONT]
 
[FONT=courier new]$ cat /etc/hosts[/FONT]
[FONT=courier new]127.0.0.1 localhost[/FONT]
[FONT=courier new]127.0.1.1 [/FONT][FONT=courier new]bob_ubuntu.domain.com [/FONT][FONT=courier new]bob_ubuntu[/FONT]
[FONT=courier new]
[/FONT][FONT=courier new]The following lines are desirable for IPv6 capable hosts[/FONT]
[FONT=courier new]::1 ip6-localhost ip6-loopback[/FONT]
[FONT=courier new]fe00::0 ip6-localnet[/FONT]
[FONT=courier new]ff00::0 ip6-mcastprefix[/FONT]
[FONT=courier new]ff02::1 ip6-allnodes[/FONT]
[FONT=courier new]ff02::2 ip6-allrouters[/FONT]
[FONT=courier new]ff02::3 ip6-allhosts[/FONT]

```Have set hostname with:
```
$ sudo hostname bob_ubuntu
hostname: the specified hostname is invalid

```But doing it this way you cant use '_' ..
Any suggestions?

Regards, cbob

---

### Post by chrislynch8 on 2010-12-08
I though you couldn't have an underscore in the hostname. Try changing the hostname to bob-ubuntu and run sudo /etc/init.d/hostname.sh start.

Then check hostname - you may need a reboot

Rgds
Chris

---

### Post by cbob on 2010-12-08
This does work, changing hostname to 'bob-ubuntu' but before my upgrade it was fine to have underscore.

I just want to reset it to the original.

/cbob

---

### Post by chrislynch8 on 2010-12-08
Seems strange that you where able to use an underscore all along. My understanding is that an underscore is an illegal character for a hostname. Is it working correctly now with the hyphen, or are you still having trouble?

I bit of info from an ibm manual 
> Avoid using the underscore (_) character in machine names. Internet standards dictate that domain names conform to the host name requirements described in ***_Internet Official Protocol Standards RFC 952 and RFC 1123_***. Domain names must contain only letters (upper or lower case) and digits. Domain names can also contain dash characters ( - ) as long as the dashes are not on the ends of the name. Underscore characters ( _ ) are not supported in the host name


Rgds
Chris

---

### Post by cbob on 2010-12-08
Change to hyphen in all places where it was an underscore and it works grate! Thanks!

Regards, cbob

---

