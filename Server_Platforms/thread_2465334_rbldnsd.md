---
title: "rbldnsd"
date: 2021-07-29
forum: Server Platforms
---

### Post by rcrcomputing on 2021-07-29
Was wondering if anyone else that has rbldnsd loaded has upgraded to focal?
When I couldn't get rbldnsd to work, did a fresh install. Same issue.

So, here's what we have.  rbldnsd now seems to run as a service. Totally broken and nothing will load on port 530 which is what i've specified.

As for the service, 
You have to put a dash in your command and will not take a name for the instance, not a issue for me.
RBLDNSD="- -r /var/lib/rbldns -b 127.0.0.1/530 \
                  ^dash

However, even though it no longer complains when attempting to start, we get this in netstat
unix  2      [ ]         DGRAM                    20236    712/rbldnsd
unix  3      [ ]         STREAM     CONNECTED     23780    712/rbldnsd

With no connection to port 530

So, finally I get it to start by running /usr/sbin/rbldnsd.wrapper
Netstat has
udp        0      0 127.0.0.1:530           0.0.0.0:*                           0          27091      1943/rbldnsd
unix  2      [ ]         DGRAM                    27090    1943/rbldnsd

Yeah,,,   anyway anyone know of a fix?  Or should I just disable the service and rig my own method of working? Would prefer it to work so upgrading later would be seamless as possible..

---

### Post by MAFoElffen on 2021-07-29
Maybe this might help(?)
[https://cwiki.apache.org/confluence/display/spamassassin/CachingNameserver](https://cwiki.apache.org/confluence/display/spamassassin/CachingNameserver)

---

### Post by rcrcomputing on 2021-08-02
Thanks for that, but had already explored it. Unsuccessfully.  :(
I finally put this in /etc/default/rbldns
SYSTEMCTL_SKIP_REDIRECT=1

Remove rbldns service
systemctl stop rbldnsd.service
systemctl stop rbldnsd.socket
systemctl disable rbldnsd.service
systemctl disable rbldnsd.socket

and in /etc/crontab 
@reboot	root /etc/init.d/rbldnsd start

Yes, it's a hack, seems to work though.

---

### Post by rcrcomputing on 2021-08-10
Just a note.  On the final upgrade run, I tried:

apt-mark hold rbldnsd

It did honor it!  Now have the previous version after upgrading and all is well.

Still had to add this to get bind dns back up.

Open /etc/bind/named.conf.options and add:

dnssec-enable yes;

dnssec-validation no;

---

### Post by MAFoElffen on 2021-08-10
Since you found a problem with the updated/current version of it and the older version works, I think it would help "everyone" if you reported it as a bug on the current version to Launchpad. It has a problem that needs to be fixed. Even for you (eventually).

---

