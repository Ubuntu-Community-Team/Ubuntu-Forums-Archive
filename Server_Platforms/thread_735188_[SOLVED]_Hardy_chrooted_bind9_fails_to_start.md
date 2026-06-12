---
title: "[SOLVED] Hardy chrooted bind9 fails to start"
date: 2008-03-25
forum: Server Platforms
---

### Post by djamu on 2008-03-25
Preparing to move my server to LTS hardy, ( just testing on a vmware )
 I've found a weird issue while chrooting bind.

What I did so far -all as root-:

```
apt-get install bind9
/etc/init.d/bind9 stop

```
changed 1st line of /etc/default/bind9 
```

vim /etc/default/bind9
> changed first line to > OPTIONS="-u bind -t /var/lib/named"

```
creating some directories & a link  to move /etc/bind to /var/lib/named/etc/bind 
creating null & random devices 
fixing permissions
```

mkdir -p /var/lib/named/etc
mkdir /var/lib/named/dev
mkdir -p /var/lib/named/var/cache/bind
mkdir -p /var/lib/named/var/run/bind/run
mv /etc/bind /var/lib/named/etc
ln -s /var/lib/named/etc/bind /etc/bind
mknod /var/lib/named/dev/null c 1 3
mknod /var/lib/named/dev/random c 1 8
chmod 666 /var/lib/named/dev/null /var/lib/named/dev/random
chown -R bind:bind /var/lib/named/var/*
chown -R bind:bind /var/lib/named/etc/bind

```
fixed /etc/default/syslogd 
```

vim /etc/default/syslogd
> SYSLOGD="-a /var/lib/named/dev/log"

```

This has always worked in the past.. but doesn't on Hardy 8.04

if I try to start > /etc/bind9 start it simply fails 
stopping it >
```

 rndc: connect failed: 127.0.0.1#953: connection refused

```

vim /var/log/syslog reveals 

```

Mar 25 08:06:57 hardy-server named[11824]: starting BIND 9.4.2 -u bind -t /var/lib/named
Mar 25 08:06:57 hardy-server named[11824]: found 1 CPU, using 1 worker thread
Mar 25 08:06:57 hardy-server named[11824]: loading configuration from '/etc/bind/named.conf'
Mar 25 08:06:57 hardy-server named[11824]: none:0: open: /etc/bind/named.conf: permission denied
Mar 25 08:06:57 hardy-server named[11824]: loading configuration: permission denied
Mar 25 08:06:57 hardy-server named[11824]: exiting (due to fatal error)
Mar 25 08:06:57 hardy-server kernel: [ 9136.933011] audit(1206428817.898:3): operation="inode_permission" request_mask="r::" denied_mask="r::" name="/var/lib/named/etc/bind/named.conf" pid=11825 profile="/usr/sbin/named" namespace="default"
```

anybody any idea ?, I've  checked permissions, locations.... and with  feisty / gutsy this just worked...

thx..

[COLOR="Red"]EDIT > this is fixed
complete procedure at my last thread post[/COLOR]

---

### Post by penguin2008 on 2008-03-31
Hi guys

I have the same problem! Is there a solution for this?
Thank you

---

### Post by djamu on 2008-04-01
Well I think I have a clue of what's going on... & undoubtedly this will pop up as soon as other admins start upgrading their servers ( or at least the ones using chroots ) ..

But since they moved this thread from the server forum ( well I understand it's hardy, but it's doomed to move back there ) and on this forum it's unlikely someone will come with a real explanation... 
( the very reason why I didn't post it here )

> Hardy Heron Development Forum

Please note that developers aren't very active here, and will most likely not receive the feedback you post here. If you'd like to notify them of bugs, please do so via the Ubuntu bug tracker. If you'd like to write specifications for possible new features, start here. 

I don't think it's a bug, most likely a feature of a new package...
So far my digging leads me to a new package ported from Suse ( ? ) >** AppArmor**.... Unfortunately I don't have much time right now.. So if someone feels like toying with it, or a good **AppArmor** howto ...

I'll take a look at it again this evening... uninstalling it seems a bad option as I want to be able to use the new featues, but just for sake off verifying, I'll try it on a Vmware snapshot...

---

### Post by djamu on 2008-04-02
Apparmor is causing this, removing ( & purging )
```
apt-get purge apparmor
```
 "fixes" the issue....
but since apparmor is a feature... this shouldn't be the right way, I'll look at the Suse site for more info...

---

### Post by taavikko on 2008-04-02
> **djamu said:**
> Apparmor is causing this, removing ( & purging )
```
apt-get purge apparmor
```
 "fixes" the issue....
but since apparmor is a feature... this shouldn't be the right way, I'll look at the Suse site for more info...

You don't have to remove apparmor, you can just disable it using tool like "sysv-rc-conf"
```
sudo apt-get install sysv-rc-conf
```

```
sudo sysv-rc-conf
```
but be careful with it!!!

And remove ticks from apparmor line.

---

### Post by djamu on 2008-04-02
Mind to tell me where I can find the ported manual, since I want to know the ins & outs of this apparmor package
Do I have to disable it for chrooting services ?, or is this just a replacemnt for chrooting ?

Thx

---

### Post by taavikko on 2008-04-02
> **djamu said:**
> Mind to tell me where I can find the ported manual, since I want to know the ins & outs of this apparmor package
Do I have to disable it for chrooting services ?, or is this just a replacemnt for chrooting ?

Thx

[https://wiki.ubuntu.com/AppArmor](https://wiki.ubuntu.com/AppArmor)
and of course **man apparmor**

---

### Post by djamu on 2008-04-02
mmm ](*,) oops sorry, couldn't find apparmor only apparmor_status & apparmor_parser did a man on those.... & it wasn't very helpfull....


:lolflag:

---

### Post by djamu on 2008-04-02
K fixed,  interesting that apparmor stuff, don't know if it makes much sense to chroot and use apparmor at the same time ... guess there's no harm either...

So for completeness the complete procedure here 
( all as root, if you don't use/have root start every line with sudo )

```
apt-get install bind9
/etc/init.d/bind9 stop
/etc/init.d/apparmor stop
vim /etc/default/bind9

```
change first line to
```
OPTIONS="-u bind -t /var/lib/named"
```
create some directories & a link to move /etc/bind to /var/lib/named/etc/bind, creating null & random devices, fixing permissions
```
mkdir -p /var/lib/named/etc
mkdir /var/lib/named/dev
mkdir -p /var/lib/named/var/cache/bind
mkdir -p /var/lib/named/var/run/bind/run
mv /etc/bind /var/lib/named/etc
ln -s /var/lib/named/etc/bind /etc/bind
mknod /var/lib/named/dev/null c 1 3
mknod /var/lib/named/dev/random c 1 8
chmod 666 /var/lib/named/dev/null /var/lib/named/dev/random
chown -R bind:bind /var/lib/named/var/*
chown -R bind:bind /var/lib/named/etc/bind
```
edit /etc/default/syslogd 
```

vim /etc/default/syslogd
> SYSLOGD="-a /var/lib/named/dev/log"

```

**now edit the bind9 apparmor profile  **

```
vim /etc/apparmor.d/usr.sbin.named
```

and change marked lines 

**[COLOR="Blue"]UPDATED[/COLOR]**

```

# vim:syntax=apparmor
# Last Modified: Fri Jun  1 16:43:22 2007
#include <tunables/global>

/usr/sbin/named {
  #include <abstractions/base>
  #include <abstractions/nameservice>

  capability net_bind_service,
  capability setgid,
  capability setuid,
  capability sys_chroot,

  # Dynamic updates needs zone and journal files rw. We just allow rw for all
  # in /etc/bind, and let DAC handle the rest > moved to /var/lib/named/etc/bind
[COLOR="Blue"]  /var/lib/named/etc/bind/* rw,[/COLOR]

  /proc/net/if_inet6 r,
  /usr/sbin/named mr,
  /var/cache/bind/* rw,
[COLOR="Blue"]  /var/lib/named/var/run/bind/run/named.pid w,
  # /var/run/bind/run/named.pid w,[/COLOR]
  # support for resolvconf
[COLOR="Blue"]  /var/lib/named/var/run/bind/named.options r,
  # /var/run/bind/named.options r,[/COLOR]

[COLOR="Blue"]# add also following lines thanks to Spezi2u 
  /var/lib/named/dev/null rw,
  /var/lib/named/dev/random rw,

[/COLOR]
}

```


if you happen to put your local zones in a subdirectory of i.e. /etc/bind don't forget to add all dirs into the apparmor file.


```

/var/lib/named/etc/bind/zones/* rw,
/var/lib/named/etc/bind/zones/external/* rw,
/var/lib/named/etc/bind/zones/internal/* rw,

```


then restart services
```

/etc/init.d/sysklogd restart
/etc/init.d/apparmor start
/etc/init.d/bind9 start

```




:popcorn:

---

### Post by jmandawg on 2008-04-03
Thanks, this solved my problem.  

DO we even need to chroot bind anymore, since it's running inside apparmor?

---

### Post by djamu on 2008-04-03
> **jmandawg said:**
> Thanks, this solved my problem.  

DO we even need to chroot bind anymore, since it's running inside apparmor?

I've got no idea... but my rudimentary understanding of running apparmor -by creating protected environments ( hats ) & setting permissions on an application level - tells me those 2 are in a way complementary ...  but not identical...

The danger here is that it might not be a 1+1=2 thing ... 
It will most likely not weaken security, but for that some of the dev's need to step up ... 

If someone knows about a package ( maybe one specifically crafted for that ) with known weaknesses I might try some things out ( injecting code etc... ) ( days are to short )

So given the fact that this is still a beta of an LTS release those kind of tests will surely be performed by people more versed ..... so until then I'll assume there's no harm either.... 

[-o<

---

### Post by djamu on 2008-07-22
updated

---

### Post by TDK800 on 2009-05-08
Thanks djamu, almost a year later and experienced the same problem on 9.04

There really should be some discussion about apparmor vs chroot.... would make life lot easier if only one or other would be required, probably would save a bit on server resources too.

---

### Post by megalt1tt on 2009-10-23
Took awhile to stumble upon this very helpful thread.

Looking at the ApparmorFAQ it appears to be yet another approach to security, be it chroot, selinux and now apparmor...sigh...

Perhaps the Apparmor devs can put a more apparent finger print in the log message when denies are logged.

---

### Post by cybercity@localhost on 2012-06-15
i also have the same problem but did not find anything weird related to apparmor
```

starting BIND 9.7.0-P1 -g
15-Jun-2012 18:09:58.266 built with '--prefix=/usr' '--mandir=/usr/share/man' '--infodir=/usr/share/info' '--sysconfdir=/etc/bind' '--localstatedir=/var' '--enable-threads' '--enable-largefile' '--with-libtool' '--enable-shared' '--enable-static' '--with-openssl=/usr' '--with-gssapi=/usr' '--with-gnu-ld' '--with-dlz-postgres=no' '--with-dlz-mysql=no' '--with-dlz-bdb=yes' '--with-dlz-filesystem=yes' '--with-dlz-ldap=yes' '--with-dlz-stub=yes' '--with-geoip=/usr' '--enable-ipv6' 'CFLAGS=-fno-strict-aliasing -DDIG_SIGCHASE -O2' 'LDFLAGS=-Wl,-Bsymbolic-functions' 'CPPFLAGS='
15-Jun-2012 18:09:58.267 adjusted limit on open files from 1024 to 1048576
15-Jun-2012 18:09:58.267 found 1 CPU, using 1 worker thread
15-Jun-2012 18:09:58.268 using up to 4096 sockets
15-Jun-2012 18:09:58.288 loading configuration from '/etc/bind/named.conf'
15-Jun-2012 18:09:58.289 /etc/bind/named.conf.options:16: missing ';' before '}'
15-Jun-2012 18:09:58.290 loading configuration: failure
15-Jun-2012 18:09:58.291 exiting (due to fatal error)

```

any solution for this?

---

### Post by jgalvin2010 on 2012-07-18
Looks like there is a configuration error in : 
/etc/bind/named.conf.options: on line 16 can you post your config of this file?

---

