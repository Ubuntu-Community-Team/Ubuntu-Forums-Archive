---
title: "content filtering queries (squid/dansguardian/squidguard)"
date: 2008-02-24
forum: Server Platforms
---

### Post by pdc124 on 2008-02-24
ive spent most of the day on trying to sort this out .
Ive installed squid  and can connect through it ( havent added transparent proxying yet) .
I apt-get installed added dansguardian. filtering works OK  - but it takes 12 minutes to start DG at boot . I suppose if i compile it from source i might get it a bit quicker - but 12 minutes  on a 2.6GHz +512 MB Ram machine  !. An installation on a 1GHz gentoo box doesnt take a noticeable time to start up -  . So what the problem with this ?  ( and I started on this because i didnt think i had the time to let gentoo crunch its way through the night compiling all this stuff!) 

I then tried squidguard. - needless to say its not working yet. 

1. im not clear on the relationship between starting/restarting squid and changes in squidguard config - do i need to restart squid each time  or is the SG config read at runtime ?
and how do i restart squid /squidguard from a commandline ?

2. in squidguard.conf ive got

dbhome /var/lib/squidguard/db
logdir /var/log/squid

are the definitions for the blocks relative  to this ? 
the default blocklist that came wit the installation is in  eg 
/var/lib/squidguard/db/blacklists/adult/{expressions|urls|domains}

the configs ive found on the web and the default that came with SG  isnt relative to dbhome  - its adult/expressions, adult/urls . should it be blacklists/adult/{expressions|urls|domains}

3. there are ACLs in squid  as well as squidguard.
 Does squidguard use these ?
if not, does squidguard ACL have to be the same as the squid definition of the same name ?

All in all a very frustrating day . if i get it all sorted i'll add it to the wiki 
 if anyone has  fully working setup id love to see the configs

---

### Post by astrotech226 on 2008-02-24
I use Dansguardian and it only takes about 5 seconds to start.  Did you install any blacklists or set up filter groups.  If the blacklist is large and you try to run 9 filter groups, yes, you are going to have problems.  I think it makes a copy of the list for each group.

I tried squidguard like you and didn't have much luck.  I did get it working, but you lose the "content" filtering that Dansguardian provides.

Do you want me to look at your DG config files?

---

### Post by jmc1024 on 2008-02-24
I have squid/squidguard running.  I may be able to help you get you setup running.  My config is pretty simple and can be seen below.

I'm a little unsure what you're asking concerning the blacklist dir tree.  Just put all the directories under /var/lib/squidguard/db.  

suidGuard does not use anything in the squid.conf and no the ACLs do not need to match.

Mark


#
# CONFIG FILE FOR SQUIDGUARD
#

dbhome /var/lib/squidGuard/db
logdir /var/log/squid

dest malware {
        urllist malware/urls
}

dest white {
        domainlist white/domains
        urllist white/urls
        expressionlist white/expressions
}

dest warez {
        domainlist warez/domains
        urllist warez/urls
        log warez.access
}

dest porn {
        domainlist porn/domains
        urllist porn/urls
        log porn.access
}

dest violence {
        domainlist violence/domains
        urllist violence/urls
        log violence.access
}

acl {
        default {
                pass white !malware !violence !warez !porn all
                redirect http://rabbitkey/cgi-bin/squidGuard.cgi?clientaddr=%a&clientname=%n&clientident=%i&srcclass=%s&targetclass=%t&url=%u
        }
}

---

### Post by pdc124 on 2008-02-25
so far its the default installation of squid, DG and SG.

how do start/stop/restart all these from the commandline ?

when Squidguard is running its using 95% of system resources (as reported by top) , so the GUI is unusable like that 

I thought id remove all the  stuff and start again with default files  - it appears that the squidGuard DB is compiled with the default installation , using a blocklist thats already there  ( which one, from where?) 

so i removed SG (apt-get remove squidGuard) and re-installed it (apt-get install) but it hasnt rewritten a squidGuard config file - it was  /etc/squid/squidGuard.conf 

So i really dont get this - it installs some defaults , but doesnt finish the job 


and why , with squid removed and both configured for direct connection , does FF connect and  konqueror doesnt ("could not connect to host")

looks lke another frustrating evening ahead ;-(

---

### Post by jmc1024 on 2008-02-25
Use 'squid -k reconfigure' to restart squid from the cmdln.   IIRC the following does the same thing: /etc/init.d/squid restart

I don't know why squidGuard would be using so many resources.  Try this kill all the squid and squidGuards processes and run squidGuard alone from the cmdln like like such:
echo "http://<some.url.ltd> 127.0.0.1 - - GET" | squidGuard -d -c /path/to/squidGuard.conf
(all on one line)

Also, running squid with debug messages turned on might shed light on the problem: squid -NCd1

I will not be around the rest of the week.  Use the squidGuard maillist for more help.  Sometimes it takes a day or so to get a reply, but they are very helpful. 

Lastly, I'm including below my note for installing squid & squidGuard.

Lastly, I can't help much with problems with squid setup, sorry.

Good luck,
Mark

---------------------------------------------------------------------------------------------
This assumes network uses 192.168.1.0/255.255.255.0

0) Install various packages.
apt-get install squid squidguard iptables
apt-get install wget # for blacklist auto download and update
apt-get install apache2 exim4 # for squidGuard.cgi

1) Add to /etc/rc.local file:
#restore the iptable rules for squid
iptables-restore < /etc/iptables.up.rules

2) Run the iptable commands:
a.1) Make this machine grab all port 80 packets and pass them to squid (port 3128)
iptables -t nat -A PREROUTING -i eth0 -p tcp -d ! 192.168.1.0/24 --dport 80 -j REDIRECT --to-port 3128
a.2) Don't include '-d ! 192.168.1.0/24' if you want to filter the server's content
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128
b) Except ports 80 & 3128 when from squid.  (Let squid access internet)
iptables -t nat -A OUTPUT -p tcp --dport 80 -m owner --uid-owner squid -j ACCEPT
iptables -t nat -A OUTPUT -p tcp --dport 3128 -m owner --uid-owner squid -j ACCEPT
c) Redirect Internet traffic from all users (other than squid and any exempt users) to the filter
iptables -t nat -A OUTPUT -p tcp --dport 80 -j REDIRECT --to-ports 3128

3) Save the rules to /etc/iptable.up.rules file:
iptable-save > /etc/iptable.up.rules

4) Set IP Forwarding on:
echo "1" > /proc/sys/net/ipv4/ip_forward

5) Add the following line to the /etc/sysctl.conf so IP forwarding is turned on after reboot
# inable ip forwarding
net.ipv4.ip_forward=1

6) Add the following directives to the /etc/squid/squid.conf file:
always_direct allow all
http_access allow localhost
http_access allow localdomain
http_access deny all
redirect_program /usr/bin/squidGuard -c /etc/squid/squidGuard.conf

7) Edit the following directives in the /etc/squid/squid.conf file:
http_port 3128 transparent    # add transparent
acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl localdomain src 192.168.1.0/255.255.255.0
acl to_localhost dst 127.0.0.0/8
acl our_networks src 192.168.1.0/24
http_access allow our_networks
http_access allow localhost
cache_effective_user proxy    # Already the default value
cache_effective_group proxy   # Already the default value
visible_hostname rabbitkey

8) Configure /etc/squid/squidGuard.conf
#
# CONFIG FILE FOR SQUIDGUARD
#

dbhome /var/lib/squidguard/db
logdir /var/log/squid/
dest warez {
        domainlist warez/domains
        urllist warez/urls
}
dest porn {
        domainlist porn/domains
        urllist porn/urls
}
acl {
        default {
                pass !warez !porn all
                redirect [http://192.168.1.22/block.html](http://192.168.1.22/block.html)
        }
}

9a) Install a blacklist database from [http://squidguard.shalla.de/Downloads/shallalist.tar.gz](http://squidguard.shalla.de/Downloads/shallalist.tar.gz)
cd /var/lib/squidguard/
tar zxvf /home/mark/Downloads/shallalist.tar.gz 

9b) The BL tarball comes with lists in BL dir, but configs like them in db, so make a link from BL to db
ln -s /var/lib/squidguard/BL /var/lib/squidguard/db

9c) Initialize blacklist database
squidGuard -C all

10) start squid with:
/etc/init.d/squid start

11) Add the following line to the /etc/services file:
squid           3128/tcp                        # squid HTTP proxy
squid           3128/udp

---

### Post by pdc124 on 2008-02-25
thanks for clearing up the  database symlink issue

ive copied your  squidGuard.conf file and then add 

redirect_program /usr/bin/squidGuard -c /etc/squid/squidGuard.conf
 to squid.conf 

root@skimanbob-desktop:/etc/squid# ls -la /etc/squid |grep conf$
-rw-------   1 root root 149369 2008-02-25 20:22 squid.conf
-rw-r--r--   1 root root    251 2008-02-25 20:18 squidGuard.conf

root@skimanbob-desktop:/etc/squid#    

then test squid  and i get this 


root@skimanbob-desktop:/etc/squid# /usr/sbin/squid  -NCd1
2008/02/25 20:22:24| Starting Squid Cache version 2.6.STABLE5 for i386-debian-linux-gnu...
2008/02/25 20:22:24| Process ID 7491
2008/02/25 20:22:24| With 1024 file descriptors available
2008/02/25 20:22:24| Using epoll for the IO loop
2008/02/25 20:22:24| Performing DNS Tests...
2008/02/25 20:22:24| Successful DNS name lookup tests...
2008/02/25 20:22:24| DNS Socket created at 0.0.0.0, port 32775, FD 5
2008/02/25 20:22:24| Adding domain home.nw from /etc/resolv.conf
2008/02/25 20:22:24| Adding nameserver 192.168.0.254 from /etc/resolv.conf
2008/02/25 20:22:24| User-Agent logging is disabled.
2008/02/25 20:22:24| Referer logging is disabled.
2008/02/25 20:22:24| Unlinkd pipe opened on FD 10
2008/02/25 20:22:24| Swap maxSize 102400 KB, estimated 7876 objects
2008/02/25 20:22:24| Target number of buckets: 393
2008/02/25 20:22:24| Using 8192 Store buckets
2008/02/25 20:22:24| Max Mem  size: 8192 KB
2008/02/25 20:22:24| Max Swap size: 102400 KB
2008/02/25 20:22:24| Local cache digest enabled; rebuild/rewrite every 3600/3600 sec
2008/02/25 20:22:24| Rebuilding storage in /var/spool/squid (CLEAN)
2008/02/25 20:22:24| Using Least Load store dir selection
2008/02/25 20:22:24| Set Current Directory to /var/spool/squid
2008/02/25 20:22:24| Loaded Icons.
2008/02/25 20:22:24| Accepting proxy HTTP connections at 0.0.0.0, port 3128, FD 12.
2008/02/25 20:22:24| Accepting ICP messages at 0.0.0.0, port 3130, FD 13.
2008/02/25 20:22:24| HTCP Disabled.
2008/02/25 20:22:24| WCCP Disabled.
2008/02/25 20:22:24| Ready to serve requests.
2008/02/25 20:22:24| Done reading /var/spool/squid swaplog (589 entries)
2008/02/25 20:22:24| Finished rebuilding storage from disk.
2008/02/25 20:22:24|       589 Entries scanned
2008/02/25 20:22:24|         0 Invalid entries.
2008/02/25 20:22:24|         0 With invalid flags.
2008/02/25 20:22:24|       589 Objects loaded.
2008/02/25 20:22:24|         0 Objects expired.
2008/02/25 20:22:24|         0 Objects cancelled.
2008/02/25 20:22:24|         0 Duplicate URLs purged.
2008/02/25 20:22:24|         0 Swapfile clashes avoided.
2008/02/25 20:22:24|   Took 0.4 seconds (1343.6 objects/sec).
2008/02/25 20:22:24| Beginning Validation Procedure
2008/02/25 20:22:24|   Completed Validation Procedure
2008/02/25 20:22:24|   Validated 589 Entries
2008/02/25 20:22:24|   store_swap_size = 3888k
2008/02/25 20:22:25| storeLateRelease: released 0 objects
2008/02/25 20:22:43| Preparing for shutdown after 0 requests
2008/02/25 20:22:43| Waiting 0 seconds for active connections to finish
2008/02/25 20:22:43| FD 12 Closing HTTP connection
2008/02/25 20:22:43| Shutting down...
2008/02/25 20:22:43| FD 13 Closing ICP connection
2008/02/25 20:22:43| Closing unlinkd pipe on FD 10
2008/02/25 20:22:43| storeDirWriteCleanLogs: Starting...
2008/02/25 20:22:43|   Finished.  Wrote 589 entries.
2008/02/25 20:22:43|   Took 0.0 seconds (373257.3 entries/sec).
2008/02/25 20:22:43| Squid Cache (Version 2.6.STABLE5): Exiting normally.
root@skimanbob-desktop:/etc/squid# /usr/sbin/squid  -NCd1
2008/02/25 20:22:45| Starting Squid Cache version 2.6.STABLE5 for i386-debian-linux-gnu...
2008/02/25 20:22:45| Process ID 7498
2008/02/25 20:22:45| With 1024 file descriptors available
2008/02/25 20:22:45| Using epoll for the IO loop
2008/02/25 20:22:45| Performing DNS Tests...
2008/02/25 20:22:45| Successful DNS name lookup tests...
2008/02/25 20:22:45| DNS Socket created at 0.0.0.0, port 32775, FD 5
2008/02/25 20:22:45| Adding domain home.nw from /etc/resolv.conf
2008/02/25 20:22:45| Adding nameserver 192.168.0.254 from /etc/resolv.conf
2008/02/25 20:22:45| helperOpenServers: Starting 5 'squidGuard' processes
2008/02/25 20:22:45| User-Agent logging is disabled.
2008/02/25 20:22:45| Referer logging is disabled.
2008/02/25 20:22:45| Unlinkd pipe opened on FD 15
2008/02/25 20:22:45| Swap maxSize 102400 KB, estimated 7876 objects
2008/02/25 20:22:45| Target number of buckets: 393
2008/02/25 20:22:45| Using 8192 Store buckets
2008/02/25 20:22:45| Max Mem  size: 8192 KB
2008/02/25 20:22:45| Max Swap size: 102400 KB
2008/02/25 20:22:45| Local cache digest enabled; rebuild/rewrite every 3600/3600 sec
2008/02/25 20:22:45| Rebuilding storage in /var/spool/squid (CLEAN)
2008/02/25 20:22:45| Using Least Load store dir selection
2008/02/25 20:22:45| Set Current Directory to /var/spool/squid
2008/02/25 20:22:45| Loaded Icons.
2008/02/25 20:22:45| Accepting proxy HTTP connections at 0.0.0.0, port 3128, FD 17.
2008/02/25 20:22:45| Accepting ICP messages at 0.0.0.0, port 3130, FD 18.
2008/02/25 20:22:45| HTCP Disabled.
2008/02/25 20:22:45| WCCP Disabled.
2008/02/25 20:22:45| Ready to serve requests.
2008/02/25 20:22:45| WARNING: url_rewriter #2 (FD 7) exited
2008/02/25 20:22:45| WARNING: url_rewriter #5 (FD 10) exited
2008/02/25 20:22:45| WARNING: url_rewriter #4 (FD 9) exited
2008/02/25 20:22:45| Too few url_rewriter processes are running
FATAL: The url_rewriter helpers are crashing too rapidly, need help!

Aborted (core dumped)
root@skimanbob-desktop:/etc/squid#

---

### Post by jmc1024 on 2008-02-25
This lines:

2008/02/25 20:22:45| WARNING: url_rewriter #5 (FD 10) exited
2008/02/25 20:22:45| WARNING: url_rewriter #4 (FD 9) exited
2008/02/25 20:22:45| Too few url_rewriter processes are running
FATAL: The url_rewriter helpers are crashing too rapidly, need help!

tell me squidGuard is failing.  Did you run squidGuard alone on the cmdln?

echo "http://some.site/ 127.0.0.1 - - GET" | squidGuard -d


Mark

---

### Post by pdc124 on 2008-02-25
thanks for clearing up the  database symlink issue

ive copied your  squidGuard.conf file and then add 

redirect_program /usr/bin/squidGuard -c /etc/squid/squidGuard.conf
 to squid.conf 

root@skimanbob-desktop:/etc/squid# ls -la /etc/squid |grep conf$
-rw-------   1 root root 149369 2008-02-25 20:22 squid.conf
-rw-r--r--   1 root root    251 2008-02-25 20:18 squidGuard.conf

root@skimanbob-desktop:/etc/squid#    

then test squid  and i get this 


root@skimanbob-desktop:/etc/squid# /usr/sbin/squid  -NCd1
2008/02/25 20:22:24| Starting Squid Cache version 2.6.STABLE5 for i386-debian-linux-gnu...
2008/02/25 20:22:24| Process ID 7491
2008/02/25 20:22:24| With 1024 file descriptors available
2008/02/25 20:22:24| Using epoll for the IO loop
2008/02/25 20:22:24| Performing DNS Tests...
2008/02/25 20:22:24| Successful DNS name lookup tests...
2008/02/25 20:22:24| DNS Socket created at 0.0.0.0, port 32775, FD 5
2008/02/25 20:22:24| Adding domain home.nw from /etc/resolv.conf
2008/02/25 20:22:24| Adding nameserver 192.168.0.254 from /etc/resolv.conf
2008/02/25 20:22:24| User-Agent logging is disabled.
2008/02/25 20:22:24| Referer logging is disabled.
2008/02/25 20:22:24| Unlinkd pipe opened on FD 10
2008/02/25 20:22:24| Swap maxSize 102400 KB, estimated 7876 objects
2008/02/25 20:22:24| Target number of buckets: 393
2008/02/25 20:22:24| Using 8192 Store buckets
2008/02/25 20:22:24| Max Mem  size: 8192 KB
2008/02/25 20:22:24| Max Swap size: 102400 KB
2008/02/25 20:22:24| Local cache digest enabled; rebuild/rewrite every 3600/3600 sec
2008/02/25 20:22:24| Rebuilding storage in /var/spool/squid (CLEAN)
2008/02/25 20:22:24| Using Least Load store dir selection
2008/02/25 20:22:24| Set Current Directory to /var/spool/squid
2008/02/25 20:22:24| Loaded Icons.
2008/02/25 20:22:24| Accepting proxy HTTP connections at 0.0.0.0, port 3128, FD 12.
2008/02/25 20:22:24| Accepting ICP messages at 0.0.0.0, port 3130, FD 13.
2008/02/25 20:22:24| HTCP Disabled.
2008/02/25 20:22:24| WCCP Disabled.
2008/02/25 20:22:24| Ready to serve requests.
2008/02/25 20:22:24| Done reading /var/spool/squid swaplog (589 entries)
2008/02/25 20:22:24| Finished rebuilding storage from disk.
2008/02/25 20:22:24|       589 Entries scanned
2008/02/25 20:22:24|         0 Invalid entries.
2008/02/25 20:22:24|         0 With invalid flags.
2008/02/25 20:22:24|       589 Objects loaded.
2008/02/25 20:22:24|         0 Objects expired.
2008/02/25 20:22:24|         0 Objects cancelled.
2008/02/25 20:22:24|         0 Duplicate URLs purged.
2008/02/25 20:22:24|         0 Swapfile clashes avoided.
2008/02/25 20:22:24|   Took 0.4 seconds (1343.6 objects/sec).
2008/02/25 20:22:24| Beginning Validation Procedure
2008/02/25 20:22:24|   Completed Validation Procedure
2008/02/25 20:22:24|   Validated 589 Entries
2008/02/25 20:22:24|   store_swap_size = 3888k
2008/02/25 20:22:25| storeLateRelease: released 0 objects
2008/02/25 20:22:43| Preparing for shutdown after 0 requests
2008/02/25 20:22:43| Waiting 0 seconds for active connections to finish
2008/02/25 20:22:43| FD 12 Closing HTTP connection
2008/02/25 20:22:43| Shutting down...
2008/02/25 20:22:43| FD 13 Closing ICP connection
2008/02/25 20:22:43| Closing unlinkd pipe on FD 10
2008/02/25 20:22:43| storeDirWriteCleanLogs: Starting...
2008/02/25 20:22:43|   Finished.  Wrote 589 entries.
2008/02/25 20:22:43|   Took 0.0 seconds (373257.3 entries/sec).
2008/02/25 20:22:43| Squid Cache (Version 2.6.STABLE5): Exiting normally.
root@skimanbob-desktop:/etc/squid# /usr/sbin/squid  -NCd1
2008/02/25 20:22:45| Starting Squid Cache version 2.6.STABLE5 for i386-debian-linux-gnu...
2008/02/25 20:22:45| Process ID 7498
2008/02/25 20:22:45| With 1024 file descriptors available
2008/02/25 20:22:45| Using epoll for the IO loop
2008/02/25 20:22:45| Performing DNS Tests...
2008/02/25 20:22:45| Successful DNS name lookup tests...
2008/02/25 20:22:45| DNS Socket created at 0.0.0.0, port 32775, FD 5
2008/02/25 20:22:45| Adding domain home.nw from /etc/resolv.conf
2008/02/25 20:22:45| Adding nameserver 192.168.0.254 from /etc/resolv.conf
2008/02/25 20:22:45| helperOpenServers: Starting 5 'squidGuard' processes
2008/02/25 20:22:45| User-Agent logging is disabled.
2008/02/25 20:22:45| Referer logging is disabled.
2008/02/25 20:22:45| Unlinkd pipe opened on FD 15
2008/02/25 20:22:45| Swap maxSize 102400 KB, estimated 7876 objects
2008/02/25 20:22:45| Target number of buckets: 393
2008/02/25 20:22:45| Using 8192 Store buckets
2008/02/25 20:22:45| Max Mem  size: 8192 KB
2008/02/25 20:22:45| Max Swap size: 102400 KB
2008/02/25 20:22:45| Local cache digest enabled; rebuild/rewrite every 3600/3600 sec
2008/02/25 20:22:45| Rebuilding storage in /var/spool/squid (CLEAN)
2008/02/25 20:22:45| Using Least Load store dir selection
2008/02/25 20:22:45| Set Current Directory to /var/spool/squid
2008/02/25 20:22:45| Loaded Icons.
2008/02/25 20:22:45| Accepting proxy HTTP connections at 0.0.0.0, port 3128, FD 17.
2008/02/25 20:22:45| Accepting ICP messages at 0.0.0.0, port 3130, FD 18.
2008/02/25 20:22:45| HTCP Disabled.
2008/02/25 20:22:45| WCCP Disabled.
2008/02/25 20:22:45| Ready to serve requests.
2008/02/25 20:22:45| WARNING: url_rewriter #2 (FD 7) exited
2008/02/25 20:22:45| WARNING: url_rewriter #5 (FD 10) exited
2008/02/25 20:22:45| WARNING: url_rewriter #4 (FD 9) exited
2008/02/25 20:22:45| Too few url_rewriter processes are running
FATAL: The url_rewriter helpers are crashing too rapidly, need help!

Aborted (core dumped)
root@skimanbob-desktop:/etc/squid#

---

### Post by pdc124 on 2008-02-25
gradually getting there!.

HowTo :


ive ended up with the dbhome path defined as 
/var/lib/squidguard/db/blacklists

squidguard -C all 

reads the path from the squidguard config file and then compiles the  database

first check the syntax of your squidGuard.conf

squidGuard -d -c /etc/squid/squidGuard.conf

once thats OK add the redirector to squid.conf

redirect_program /usr/bin/squidGuard -c /etc/squid/squidGuard.conf
 once  thats OK check the rest of the squid config 

/usr/sbin/squid  -NCd1   

and once thats OK start it up and see what happens 

webmin doesnt seem happy with the new path for the blacklist files - just trying to sort that out 

thanks for the help

---

### Post by jmc1024 on 2008-02-25
I'm telling you, forget about squid until you know you have squidGaurd setup and running.  

As su run:

          echo "http://some.site/ 127.0.0.1 - - GET" | squidGuard -d

substituting some.site with a url that is in a blacklist you have in your squidGuardconf file.  Yo may need to add '-c /path/to/conf' to the above command.

Mark

---

