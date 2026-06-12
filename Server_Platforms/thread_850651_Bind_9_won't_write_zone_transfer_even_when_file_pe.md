---
title: "Bind 9 won't write zone transfer even when file permssions are OK"
date: 2008-07-05
forum: Server Platforms
---

### Post by BobD on 2008-07-05
I've set up a new master server, with a few master zones, one of them named "internal". I have given a second server permission to do a zone transfer, and configured that second server to do so. I have more or less followed the instructions given here:

[http://www.howtoforge.com/debian_bind9_master_slave_system](http://www.howtoforge.com/debian_bind9_master_slave_system)

on setting this all up. The trouble starts when I start up bind on the slave system. While it is able to transfer the zone data, it refuses to write it out, saying it does not have permission to do so. Doing some Googling, I find that this is a common enough problem, and the cause is usually that the permissions are wrong on the the directory where the zone file is to be written. In my case, however, as far as I can tell the permissions are correct; see the transcript from the slave system below. I'm able to write to the directory as the bind account, but when named -u bind is run, an open on a file in that directory fails with an EACCES.

I expect that I'm just missing something stupid, but I'm really baffled here. Thanks for any insight anyone can offer.

root@web3:/etc/bind# cat named.conf.local
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";
zone "internal" {
        type slave;
        file "/etc/bind/zones/internal";
        masters { 10.0.12.92; };
        allow-notify { 10.0.12.92; };
};
root@web3:/etc/bind# ls -la /etc/bind
total 60
drwxrwsr-x  4 bind bind 4096 2008-07-05 19:31 .
drwxr-xr-x 74 root root 4096 2008-07-05 19:29 ..
-rw-rw-r--  1 bind bind  237 2008-04-09 15:44 db.0
-rw-rw-r--  1 bind bind  271 2008-04-09 15:44 db.127
-rw-rw-r--  1 bind bind  237 2008-04-09 15:44 db.255
-rw-rw-r--  1 bind bind  353 2008-04-09 15:44 db.empty
-rw-rw-r--  1 bind bind  270 2008-04-09 15:44 db.local
-rw-rw-r--  1 bind bind 2878 2008-04-09 15:44 db.root
-rw-rw----  1 bind bind 1145 2008-07-05 15:27 named.conf
-rw-rw-r--  1 bind bind  317 2008-07-05 19:31 named.conf.local
-rw-rw-r--  1 bind bind  765 2008-07-05 15:05 named.conf.options
drwxrwsr-x  2 bind bind 4096 2008-07-05 15:03 original-files
-rw-rw----  1 bind bind   77 2008-07-05 14:52 rndc.key
drwxrwsr-x  2 bind bind 4096 2008-07-05 19:30 zones
-rw-rw-r--  1 bind bind 1317 2008-04-09 15:44 zones.rfc1918
root@web3:/etc/bind# ls -la /etc/bind/zones
total 8
drwxrwsr-x 2 bind bind 4096 2008-07-05 19:30 .
drwxrwsr-x 4 bind bind 4096 2008-07-05 19:31 ..
root@web3:/etc/bind# sudo -u bind bash
bind@web3:/etc/bind$ id
uid=108(bind) gid=118(bind) groups=118(bind)
bind@web3:/etc/bind$ echo foo >/etc/bind/zones/bar
bind@web3:/etc/bind$ ls -la /etc/bind/zones
total 12
drwxrwsr-x 2 bind bind 4096 2008-07-05 19:35 .
drwxrwsr-x 4 bind bind 4096 2008-07-05 19:31 ..
-rw-r--r-- 1 bind bind    4 2008-07-05 19:35 bar
bind@web3:/etc/bind$ cat /etc/bind/zones/bar
foo
bind@web3:/etc/bind$ rm /etc/bind/zones/bar
bind@web3:/etc/bind$ exit
exit
root@web3:/etc/bind# /usr/sbin/named -u bind -g 
05-Jul-2008 19:38:12.982 starting BIND 9.4.2 -u bind -g
05-Jul-2008 19:38:12.983 found 1 CPU, using 1 worker thread
05-Jul-2008 19:38:12.988 loading configuration from '/etc/bind/named.conf'
05-Jul-2008 19:38:12.989 listening on IPv6 interfaces, port 53
05-Jul-2008 19:38:12.994 listening on IPv4 interface lo, 127.0.0.1#53
05-Jul-2008 19:38:12.996 listening on IPv4 interface eth0, 10.0.12.83#53
05-Jul-2008 19:38:13.009 automatic empty zone: 254.169.IN-ADDR.ARPA
05-Jul-2008 19:38:13.009 automatic empty zone: 2.0.192.IN-ADDR.ARPA
05-Jul-2008 19:38:13.009 automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
05-Jul-2008 19:38:13.010 automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
05-Jul-2008 19:38:13.010 automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
05-Jul-2008 19:38:13.010 automatic empty zone: D.F.IP6.ARPA
05-Jul-2008 19:38:13.010 automatic empty zone: 8.E.F.IP6.ARPA
05-Jul-2008 19:38:13.011 automatic empty zone: 9.E.F.IP6.ARPA
05-Jul-2008 19:38:13.011 automatic empty zone: A.E.F.IP6.ARPA
05-Jul-2008 19:38:13.011 automatic empty zone: B.E.F.IP6.ARPA
05-Jul-2008 19:38:13.021 command channel listening on 127.0.0.1#953
05-Jul-2008 19:38:13.021 command channel listening on ::1#953
05-Jul-2008 19:38:13.022 ignoring config file logging statement due to -g option
05-Jul-2008 19:38:13.023 zone 0.in-addr.arpa/IN: loaded serial 1
05-Jul-2008 19:38:13.024 zone 127.in-addr.arpa/IN: loaded serial 1
05-Jul-2008 19:38:13.026 zone 255.in-addr.arpa/IN: loaded serial 1
05-Jul-2008 19:38:13.027 zone localhost/IN: loaded serial 2
05-Jul-2008 19:38:13.028 running
05-Jul-2008 19:38:13.030 zone internal/IN: Transfer started.
05-Jul-2008 19:38:13.031 transfer of 'internal/IN' from 10.0.12.92#53: connected using 10.0.12.83#39008
05-Jul-2008 19:38:13.033 dumping master file: /etc/bind/zones/tmp-J19EG8hQOo: open: permission denied
05-Jul-2008 19:38:13.033 transfer of 'internal/IN' from 10.0.12.92#53: failed while receiving responses: permission denied
05-Jul-2008 19:38:13.033 transfer of 'internal/IN' from 10.0.12.92#53: end of transfer
05-Jul-2008 19:38:15.888 shutting down
05-Jul-2008 19:38:15.888 stopping command channel on 127.0.0.1#953
05-Jul-2008 19:38:15.888 stopping command channel on ::1#953
05-Jul-2008 19:38:15.889 no longer listening on ::#53
05-Jul-2008 19:38:15.889 no longer listening on 127.0.0.1#53
05-Jul-2008 19:38:15.889 no longer listening on 10.0.12.83#53
05-Jul-2008 19:38:15.896 exiting
root@web3:/etc/bind# strace -f named -u bind -g
[...]
[pid 13287] open("/etc/bind/zones/tmp-xDsRXEpIPD", O_RDWR|O_CREAT|O_EXCL, 0666) = -1 EACCES (Permission denied)
[...]


Both of the systems described above are running 8.04 server in kvm virtual machines on the same base server, which is also running 8.04. Both systems are running the official bind9 1:9.4.2-10 package installed with an apt-get. I seriously doubt there's any relevance, but for completeness, the kvm base system is amd64; the virtualized master server is running an i386 image (a commercial software compatibility issue) while the virtualized slave server is running an amd64 image.

---

### Post by RealPSL on 2008-07-06
I have to wonder if this may be related to apparmor. The default apparmor configuration in /etc/apparmor.d/usr.sbin.named does not give access to write in /etc/bind. Can you temporarily stop apparmor and see if it works.```
/etc/init.d/apparmor stop
```

---

### Post by rrenomeron on 2008-07-06
I was having this exact same problem, and turning off apparmor solved the problem.  Guess it's time to file a bug against apparmor.

---

### Post by BobD on 2008-07-06
> **RealPSL said:**
> I have to wonder if this may be related to apparmor. The default apparmor configuration in /etc/apparmor.d/usr.sbin.named does not give access to write in /etc/bind. Can you temporarily stop apparmor and see if it works.

Bingo! that did it. Thanks, RealPSL & rrenomeron. I'd be happy to file the bug unless one of y'all would like to do it -- let me know.

---

### Post by RealPSL on 2008-07-08
It is not a bug apparmor is acting as expected. If you look in /etc/apparmor.d you will see what it allows and the new directory you created is not in the list. If you put it in the list and parse the files it will work fine.

---

### Post by windependence on 2008-07-09
IMHO, apparmor isn't worth the trouble for the benefits you get. It can cause many problems that are not apparent to even an experienced user. It is a nice idea, but too paranoid for me. All my installs have apparmor or SE linux turned off.

-Tim

---

### Post by BobD on 2008-07-09
> **RealPSL said:**
> It is not a bug apparmor is acting as expected. If you look in /etc/apparmor.d you will see what it allows and the new directory you created is not in the list. If you put it in the list and parse the files it will work fine.

Thanks, RealPSL, for this explanation. I'm coming from a Fedora/RHEL background (actually, extending back to Slackware, SLS & TAMU, but that's for another day...) so apparmor is new to me [and SElinux remains a cipher :-( ]. I took a look at apparmor's bind configuration and see that it is set up so that one should be putting slave zone files in /var/cache/bind. I changed my named.conf.local to point to there, restarted apparmor and bind, and now all is well and proper. So if there is a "bug", it is probably in the possible lack of a solid HOWTO for setting up a bind 9 master/slave pair in Hardy (and possibly, the lack of useful diagnostics in syslog). I will attempt to leave a comment on the Debian HOWTO that I used to mention that Ubuntu slave zones should be dropped into /var/cache.

Again, thanks much for your help.

Windependence, I disagree with your contention that these things are not useful. I think that the general opacity of SElinux makes it of limited use simply because it is so hard to use that few people can take proper advantage of it. Now having had a quick look at apparmor's configuration syntax, it seems as if it has real possibilities.

--BobD

---

### Post by craig.taverner on 2008-07-15
After reading a couple of dozen articles on the internet insisting that my file permissions were wrong, I finally found this thread which not only solved my problem, but directed me to conform better to newer file location standards. I think apparmor is not bad, just unfamiliar, and this is the first time it has affected me enough to learn something about it.

I noticed that the apparmor config referenced the bind9/README.Debian.gz file and taking a peek at that, it is explicitly stated in many places that the correct location for temporary and slave files is /var/cache/bind.

:KS Thanks to RealPSL for pointing us in the right direction!

---

### Post by DonThompson on 2008-07-21
Thank you.
Thank you RealPSL for pointing to the problem.
Thank you BobD for moving me from 'working fix' to 'proper' standard installation.

Now if someone could just update [https://help.ubuntu.com/8.04/serverguide/C/dns-configuration.html](https://help.ubuntu.com/8.04/serverguide/C/dns-configuration.html)
We would be off and running.  

Or was it my own fault for putting in complete paths for file names???

---

