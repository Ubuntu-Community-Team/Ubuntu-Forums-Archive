---
title: "DDNS-updates - Ubuntu Server 8.04 + BIND9 + dhcp3-server"
date: 2008-06-10
forum: Server Platforms
---

### Post by slimjim8094 on 2008-06-10
I have an Ubuntu server 8.04 with BIND9 and dhcp3-server set up. BIND is authoritative for my router's addresses and its own, but I'd like to enable ddns-updates to put the dynamically-assigned computer hostnames into DNS.

I've tried a couple of things. At this point, my error (daemon.log) is:
```
Jun 10 17:40:57 myserv named[7016]: client 127.0.0.1#53809: updating zone 'mynet/IN': error: journal open failed: unexpected error
```

I'm really looking forward on how to get this working... thanks in advance

---

### Post by inphektion on 2008-06-10
you have any apparmor profiles for named loaded?  where is this setup in /etc/bind/mynet?

---

### Post by slimjim8094 on 2008-06-11
Oh, wow - didn't realize it came enabled by default! I disabled it
```
sudo /etc/init.d/apparmor stop
``` for now... but it looks like I can change the usr.sbin.named profile to fix it.

I think that fixed it!Thanks

---

### Post by inphektion on 2008-06-11
Yea I didn't realize either till my upgrade to hardy threw some errors for me in bind too.  
You can set aa-complain /usr/sbin/named or something to see where it's going and then lock it down aa-enforce.

---

### Post by slimjim8094 on 2008-06-11
OK, different error

```
Jun 11 10:34:43 myserver named[7016]: client 127.0.0.1#36783: updating zone 'mynet/IN': error: journal open failed: no more
```

Looks like a truncated error -but it's definitely different after turning off apparmor.

I'll mess around a bit more.

---

### Post by inphektion on 2008-06-11
where do you have this zone?  make sure there is read access for bind there. or even write if its master

---

### Post by slimjim8094 on 2008-06-11
user 'bind' is the owner of all of /etc/bind/, ug+rw

---

### Post by inphektion on 2008-06-11
seems like then your bind isn't running as bind...
take a look in /etc/default/bind9 and see if you have:
```
OPTIONS="-u bind"
```
If not, add it and problem should resolve itself.

---

### Post by slimjim8094 on 2008-06-15
Problem was apparmor, disabling it fixed the problem

I was running as -u bind.

New question: my fixed DHCP clients aren't in DNS - only the dynamic ones... I'd rather have it be a ddns-update in case I want to add/change the IP.

Any guesses?

---

### Post by cviniciusm on 2008-06-21
Hello,

From /usr/share/doc/bind9/README.Debian.gz :
"
...
Zones subject to automatic updates via DHCP should be stored in /var/lib/bind,
and specified with full pathnames.
...
Apparmor Profile
----------------
If your system uses apparmor, please note that the shipped enforcing profile
works with the default installation, and changes in your configuration may
require changes to the installed apparmor profile. Please see
[https://wiki.ubuntu.com/DebuggingApparmor](https://wiki.ubuntu.com/DebuggingApparmor) before filing a bug against this
software.
"

I have implemented DHCP with dynamic updates on DNS by:
a) created the zone file on /var/lib/bind;
b) created an updater key through dnssec-keygen and put it in the zone file;
c) put the updater key int the file dhcpd.conf .

So, it works with apparmor on.


Regards,
cviniciusm.

---

### Post by xdracco on 2012-09-11
I was having the same exact error (error: journal open failed: unexpected error). Apparmor was /not/ the issue, in fact, apparmor defaults for bind are just fine. The issue was that I was not telling my zone where to write the journal file to.....

So, to fix this error, tell your zone where to write the journal..

Example name.conf.options zone:
```
zone "domain.lan" IN {
        type master;
        file "/etc/bind/zone.domain.lan";
        journal "/var/lib/bind/zone.domain.lan.jnl";
        check-names ignore;
        allow-update { key DHCP_UPDATER; };
};
```You'll need to declare the journal parameter in the reverse zone as well.

After making changes, reboot bind and you'll start seeing DDNS working.

Hope this helps someone.

---

