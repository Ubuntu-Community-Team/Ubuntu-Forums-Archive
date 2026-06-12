---
title: "HowTo Install a DJBdns cache in Ubuntu Linux"
date: 2008-10-23
forum: Server Platforms
---

### Post by docplastic on 2008-10-23
HowTo Install DJBdns in Ubuntu Linux

DJBdns <http://cr.yp.to/djbdns.html> are a set of tools to retrieve and publish Domain Name System (DNS) information.
Its main applications are a local DNS cache (dnscache) and an authoritarive DNS server (tinydns).

[Posted at <http://ubuntuforums.org/showthread.php?t=956864>]

**1. Prepare to install**
# The djbdns services need daemontools and ucspi-tcp supporting packages.

# Install tools used to build djbdns
sudo aptitude install -R build-essential


**2. Install daemontools**
# daemontools [http://cr.yp.to/daemontools.html](http://cr.yp.to/daemontools.html) is a collection of tools to manage OS services (much like init.d or upstart).

# we will force daemontools to install its binaries at /var/command/
cd $(mktemp -d) # create a temp dir and cd into it
wget http://cr.yp.to/daemontools/daemontools-0.76.tar.gz
tar xpzf daemontools-0.76.tar.gz

sudo touch /etc/inittab # daemontools install needs to see a /etc/inittab file

# build and install daemontools
cd admin/daemontools-0.76
# force binaries to install at /var/command/ and /var/service/
sed -i 's/^extern\ int\ errno\;/#include\ \<errno.h\>/' src/error.h
sed -i 's/ \/command/ \/var\/command/g;s/ln -s $parent/cp -a $parent/g' package/upgrade
sed -i 's/\/command/\/var\/command/g;s/\/service/\/var\/service/g' src/svscanboot.sh
sed -i 's/\/command/\/var\/command/g;s/\/service/\/var\/service/g' package/run
sudo package/install
sudo rm -rf /etc/inittab

# Ubuntu >=9.10: create upstart file to keep daemontools services up
sudo tee /etc/init/svscanstarter.conf <<-\EOA
# /etc/init/svscanstarter.conf
# svscanstarter - keep up daemontools 'svscan /var/service'
description "svscanstarter keep up daemontools"
start on runlevel [2345]
stop on runlevel [!2345]
respawn
exec /var/command/svscanboot
EOA

sudo start svscanstarter # to stop it use: sudo stop svscanstarter
sudo status svscanstarter # check status
ps -ef | sed '/!d/d;/svscan/!d' # check svscanboot/svscan processes

# add a command to clear the service errors log
sudo rm -rf /etc/clear /var/service/clear && sudo mkdir -p /etc/clear
sudo touch /etc/clear/down && sudo chmod a-w /etc/clear/down
sudo tee /etc/clear/run <<-\EOA
#!/bin/sh
# to check for service errors execute:
#    ps -ef | sed '/!d/d;/readproctitle/!d'
# to clear the service error log execute:
#    sudo svc -o /var/service/clear
yes '' | head -400 | tr '\n' .
EOA
sudo chmod +x /etc/clear/run
sudo ln -svf /etc/clear /var/service/;sleep 3 # start clear (using daemontools)
sudo svstat /var/service/* /var/service/*/log # check status


**3. Install ucspi-tcp**
# ucspi-tcp [http://cr.yp.to/ucspi-tcp.html](http://cr.yp.to/ucspi-tcp.html) is a collection of tools to manage TCP client-server applications
# it includes: a tcpserver, a tcpclient, and command line tools to build client-server apps.

# ucspi-tcp binaries will be installed at:  /usr/local/bin/
wget http://cr.yp.to/ucspi-tcp/ucspi-tcp-0.88.tar.gz
tar xzf ucspi-tcp-0.88.tar.gz
cd ucspi-tcp-0.88
sed -i 's/^extern\ int\ errno\;/#include\ \<errno.h\>/' error.h
make
# on AMD64, errors may show up related to a gcc bug (Google for it)
#    see [http://marc.info/?l=qmail&m=111725518121864&w=2](http://marc.info/?l=qmail&m=111725518121864&w=2)
sudo make setup check


**4. Install djbdns**
# djbdns binaries will be installed at:  /usr/local/bin/
wget http://cr.yp.to/djbdns/djbdns-1.05.tar.gz
tar xzf djbdns-1.05.tar.gz

# we use riemann's dumpcache patch [http://riemann.fmi.uni-sofia.bg/docs/djbdns-dumpcache.html](http://riemann.fmi.uni-sofia.bg/docs/djbdns-dumpcache.html) to be able to save/load the dns cache to/from hard disk
wget http://riemann.fmi.uni-sofia.bg/programs/djbdns-dumpcache.patch
# change the default save-to-disk interval from from 4h (14400s) to 5m (300s)
sed -i 's/14400/300/' djbdns-dumpcache.patch
cd djbdns-1.05
patch < ../djbdns-dumpcache.patch

# fix SIGPIPE bug: make dnscache ignore the SIGPIPE signal
(n=$'\n' ; egrep 'signal.h|SIGPIPE' dnscache.c || sed -i -e "/^#include \"env.h\"/i\\${n}#include <signal.h>" -e "/env_get(\"IP\")/i\\${n}  signal(SIGPIPE, SIG_IGN);" dnscache.c)
# fix CVE-2009-0858 (Dempsky) bug: [http://article.gmane.org/gmane.network.djbdns/13864](http://article.gmane.org/gmane.network.djbdns/13864)
sed -i '/dlen <= 128/s/if (dlen <= 128)/if ((dlen <= 128) \&\& (response_len < 16384))/' response.c
# fix gcc errno bug
sed -i 's/^gcc -O2/& -include \/usr\/include\/errno.h/' conf-cc

sudo make setup check # install djbdns binaries

# Update list of available dns root servers
# latter, dnscache-conf will copy these to /var/service/dnscache/root/servers/@
dnsip $(dnsqr ns . | sed -e '/answer/!d;s/\(.*\)NS \(.*\)/\2/') | sudo tee /etc/dnsroots.global

# Check if the dnscache tools are working:
#    a) send a query to a DNS server somewhere at the Internet
dnsq a www.google.com 192.203.230.10
#    b) send a query to an upstream DNS cache
env DNSCACHEIP=208.67.222.222 dnsqr a www.google.com


**5. Configure & start dnscache**
# add djbdns group and users
sudo groupadd djbdns
sudo useradd -d /dev/null -s /bin/false -g djbdns dnslog # unprivileged user
sudo useradd -d /dev/null -s /bin/false -g djbdns dnscache # unprivileged user
grep dns /etc/group /etc/passwd # check them

# set up a dnscache service chrooted in the /etc/dnscache directory:
sudo dnscache-conf dnscache dnslog /etc/dnscache

sudo ln -svf /etc/dnscache /service # start and keep up dnscache

#<optional> To let other computers use this dnscache, just touch their IP;
# You may authorize several clients/networks by touching several IP/IPranges
# Single IP like 192.168.2.7, or IPrange like 192.168 (NO TRAILING DOT)
# sudo touch /var/service/dnscache/root/ip/192.168.2.7
# sudo touch /var/service/dnscache/root/ip/10.0.0

#<optional>  if you need to restore a saved cache from a previous backup, use:
sudo cp -vau /some_backup_source/data /etc/dnscache/root/dump/

# **If your computer uses DHCP** to obtain a dynamically assigned IP address, configure the DHCP client to use dnscache (listening at 127.0.0.1):
sudo sed -i -e '/prepend/s/#//;/prepend/s/domain-name-servers\(.*\)/domain-name-servers 127\.0\.0\.1;/' /etc/dhcp3/dhclient.conf

# **If your computer uses a static IP address**, the FIRST LINE in /etc/resolv.conf must be: nameserver 127.0.0.1
grep -q 'nameserver 127.0.0.1' /etc/resolv.conf || (n=$'\n' ; sudo sed -i -e "1i\\${n}nameserver 127.0.0.1" /etc/resolv.conf)

# restart networking services
sudo dhclient;sleep 2 # if using DHCP (just need to renew the dhcp lease)
sudo /etc/init.d/networking restart # or, if using static IP


**6. Control dnscache**
# check service status
sudo svstat /var/service/* /var/service/*/log
(cd /var/service/dnscache/env 2>&1>/dev/null && grep "^" * ) # show env & config
(cd /var/service/dnscache/root/ip 2>&1>/dev/null && ls -1 ) # show authorised clients
(cd /var/service/dnscache/root/servers 2>&1>/dev/null && grep "^" /dev/null * ) # show root servers

# commands to control dnscache
sudo svc -d /var/service/dnscache;sudo svc -u /var/service/dnscache # restart
sudo svc -d /var/service/dnscache # down: stop and keep down
sudo svc -u /var/service/dnscache # up: (re)start
sudo svc -t /var/service/dnscache # dump cache and exit

# if compiled using the riemann's dumpcache patch
sudo svc -t /var/service/dnscache ;# dump & reload
sudo svc -a /var/service/dnscache ;# dump cache
sudo svc -h /var/service/dnscache ;# (re)load cache
# disable riemann's dumpcache resizing:
sudo -u dnscache -s ln -svf 0:0 /var/service/dnscache/root/dump/data.blowup

# cache logging: enable log of cached IPs (default):
grep 'multilog' /etc/dnscache/log/run
sudo sed -i 's/multilog.*/multilog t \.\/main/' /etc/dnscache/log/run
sudo svc -h /var/service/dnscache/log ;# restart log service
# cache logging: disable log of cached IPs
grep 'multilog' /etc/dnscache/log/run
sudo sed -i 's/multilog.*/multilog -*/' /etc/dnscache/log/run
sudo svc -h /var/service/dnscache/log ;# restart log service
# change logging:
# add stats: exec setuidgid dnslog multilog t '-*' +'*stats *' ./main
# add s+d+s: exec setuidgid dnslog multilog t '-*' +'*stats *' +'*dump *' +'*slurp *' ./main

# error logging: check status & clear
ps -ef | sed '/!d/d;/readproctitle/!d' # check for service errors
sudo svc -o /var/service/clear # clear service errors log
# error logging: enable error logging (default)
# sed -i 's/exec\ \&\>\/dev\/null/exec\ 2\>\&1/' /var/service/dnscache/run
# sudo svc -d /var/service/dnscache;sudo svc -u /var/service/dnscache # restart
# error logging: disable error logging (if no need to debug dnscache):
grep -i 'exec' /var/service/dnscache/run
# sed -i 's/exec\ 2>\&1/exec\ \&\>\/dev\/null/' /var/service/dnscache/run
# sudo svc -d /var/service/dnscache;sudo svc -u /var/service/dnscache # restart

**# Update root dns servers**
dnsip $(dnsqr ns . | sed -e '/answer/!d;s/\(.*\)NS \(.*\)/\2/') | sudo tee /etc/dnsroots.global
sudo cp -v /etc/dnsroots.global /etc/dnscache/root/servers/@'{NEW}'
sudo mv /etc/dnscache/root/servers/@'{NEW}' /etc/dnscache/root/servers/@

**7. Test dnscache**
# confirm that resolv.conf first directive is nameserver 127.0.0.1
head /etc/resolv.conf

# Test if dnscache is working:
dnsip www.fsf.org
dnsqr any cnn.com

# IF  dnscache CACHE LOGGING enabled:
# Open 2 terminals side-by-side (press ALT+F2 and enter: gnome-terminal)
# in terminal 1, check dnscache working:
tail -f /var/service/dnscache/log/main/current
# in terminal 2, compare "Query time" from both runs:
dig google.com | grep time && sleep 2 && \
dig google.com | grep time


**Ubuntu Desktop users will want to stop here.**
**==================================================**


[B]Ubuntu System administrators in charge with Internet or Intranet domain name publishing,
will find the following procedure much more simple than the BIND way.[/B]

**8. Install tinydns**
# add tinydns (unprivileged) user
sudo useradd -d /dev/null -s /bin/false -g djbdns tinydns
grep tinydns /etc/passwd # check if user tinydns was created

# subsitute IP for your server name IP (as in 123.123.123.123)
sudo tinydns-conf tinydns dnslog /etc/tinydns IP

# start tinydns (after a 5 second delay)
sudo ln -svf /etc/tinydns /etc/service

# To get started, try the add-* utilities.
#  More experienced users will prefer to directly edit the /etc/tinydns/root/data file.

# To add a NS record, establishing this server as the nameserver for your domain:
cd /etc/service/tinydns/root
sudo ./add-ns example.org 1.2.3.4

# To add hostname records for your domain:
sudo ./add-host alice.example.org 1.2.3.4
sudo ./add-host betty.example.org 1.2.3.5
sudo ./add-host carol.example.org 1.2.3.6

# To add a mailserver for your domain, add an MX record:
sudo ./add-mx example.org 1.2.3.4

# To add some aliases:
sudo ./add-alias [www.example.org]("http://www.example.org") 1.2.3.5

# Commit the changes. This compiles the plain-text data file into data.cdb and the changes will be available to tinydns immediately, without the need to restart the service:
sudo make

# To check if the server is working:
dnsq ns example.org 1.2.3.4
dnsq a betty.example.org 1.2.3.4
dnsq mx example.org 1.2.3.4

# See bellow: "TinyDNS configuration examples"

**9. TinyDNS configuration examples**
[http://www.thedjbway.org/djbdns/tinydns-intl.html](http://www.thedjbway.org/djbdns/tinydns-intl.html)

# tinydns/root/data
# example.org
# ===
###
### SOA (SOA/NS/A):
.example.org:1.2.3.4:a:259200
### HOST (A/PTR):
=fluxe.example.org:1.2.3.4:86400
### MX (MX/A):
@example.org:1.2.3.4:mailhub.example.org:0:86400
### ALIAS (A):
+[www.example.org:1.2.3.4:86400]("http://www.example.org:1.2.3.4:86400")
#
### etheropia:
###
### HOST (A only):
+ether.example.org:66.77.11.33:86400
+ep.example.org:66.77.11.33:86400
+ether.ep.example.org:66.77.11.33:86400
### MX (MX/A) maildrop here:
@ep.example.org:1.2.3.4:maildrop.ep.example.org:0:86400
#
### gnubia:
###
### HOST (A only):
+gnubi.example.org:112.211.212.121:86400
+gx.example.org:112.211.212.121:86400
+gnubi.gx.example.org:112.211.212.121:86400
### MX (MX/A) primary:
@gx.example.org:112.211.212.121:a:0:86400
### MX (MX/A) backup maildrop here:
@gx.example.org:1.2.3.4:maildrop.gx.example.org:10:86400
### ALIAS (A, gnubi own web IT-Ubuntu:IT-Main:Software:Server):
+[www.gx.example.org:112.211.212.121:86400]("http://www.gx.example.org:112.211.212.121:86400")
#
### hackistan:
###
### HOST (A only):
+hacki.example.org:90.80.70.60:86400
### NS delegation (NS/A):
&hs.example.org:90.80.70.60:a:259200
#
# tinydns/root/data
# hs.example.org
# ===
###
### SOA (SOA/NS/A):
.hs.example.org:90.80.70.60:a:259200
### HOST (A/PTR):
=hacki.hs.example.org:90.80.70.60:86400
### MX (MX/A):
@hs.example.org:90.80.70.60:a:0:86400
### ALIAS (A):
+[www.hs.example.org:90.80.70.60:86400]("http://www.hs.example.org:90.80.70.60:86400")

**10. Download and install publicfile**
Publicfile supplies files to the public through HTTP and FTP. 
Home: [http://cr.yp.to/publicfile.html](http://cr.yp.to/publicfile.html)

Install notes: [http://cr.yp.to/publicfile/install.html](http://cr.yp.to/publicfile/install.html)

wget http://cr.yp.to/publicfile/publicfile-0.52.tar.gz
tar xzf publicfile-0.52.tar.gz
cd publicfile-0.52
make
sudo make setup check

**11. Interesting files and directories**
ls -la /command/* # daemontools binaries
ls -la /usr/local/bin/* # binaries
cat /command/svscanboot # script that starts the supervisor

ls -la /service/*   # supervised services
ls -la /service/*/log # supervised services log files

**12. Uninstall it all**
sudo svc -dx /service/dnscache
sudo svc -dx /service/tinydns
sudo initctl stop svscanstarter
sudo rm /etc/event.d/svscanstarter
test -x /usr/local/bin/dnscache && sudo rm /usr/local/bin/dnscache

# :todo: remove daemontools, ucspi-tcp and djbdns files

sudo userdel -rf dnscache
sudo userdel -rf dnslog
sudo userdel -rf tinydns
sudo groupdel djbdns
sudo rm -rf /service /command /etc/dnscache /etc/tinydns

sudo dhclient # if using dinamic IP (DHCP), renew the dhcp lease
sudo /etc/init.d/networking restart # if using static IP

**13. Reference**
a) Documentation and Man pages are available at: http://smarden.org/pape/djb/
wget -c http://smarden.org/pape/Debian/dists/woody/unofficial/binary-i386/daemontools-doc_0.76-3_all.deb
wget -c http://smarden.org/pape/Debian/dists/woody/unofficial/binary-i386/ucspi-tcp-doc_0.88-5_all.deb
wget -c http://smarden.org/pape/Debian/dists/woody/unofficial/binary-i386/djbdns-doc_1.05-4_all.deb
sudo dpkg -i daemontools-doc_0.76-3_all.deb
sudo dpkg -i ucspi-tcp-doc_0.88-5_all.deb
sudo dpkg -i djbdns-doc_1.05-4_all.deb
b) djbdns: More Than Just a Mouthful of Consonants <http://www.linuxjournal.com/article/10112>
c) Quick & Dirty Guide to djbDNS <http://www.fredshack.com/docs/djbdns.html>
d) How to adjust cache size <http://cr.yp.to/djbdns/cachesize.html>
e) Perfect DjbDNS Setup On Ubuntu Server 8.04 (amd64) Hardy <http://www.howtoforge.com/perfect-djbdns-setup-on-ubuntu8.04-amd64>
f) Install Djbdns on Ubuntu Server <http://www.rasyid.net/2008/07/08/install-djbdns-on-ubuntu-server/>
g) For an Debian/Ubuntu way to install djbdns, i.e. using "sudo apt-get install daemontools djbdns qmail cvm" see: [http://smarden.org/pape/Debian/djbdns.html](http://smarden.org/pape/Debian/djbdns.html)

---

### Post by LOG123 on 2008-10-23
cool! :D

---

### Post by Mach1US on 2008-12-14
I have gotten DJBDNS up and running on 8.04 , i have copied Data file from tiny installation on another server( gentoo) which was configured about 5 years ago by admin which is no longer with us and to my surprise everything started working fine until i tried to update the data file with new entry .
I have issued make command like before but now any of new entries are just unreachable (everything else is working fine) from any machine using this new DNS.
But the same entry  upon make on the old server (running Gentoo) is resolving without a problem.
I did refreshed the cache , even did entire reboot but still nothing.
       Any ideas ???

---

### Post by jAIk on 2009-07-07
Hello Ubuntuusers,

thank you docplastic for this guide.


At the end of point number 4 I've a problem. I don't know much about DNS or DJBDNS, so it might be a very simple problem:

sudo make setup check

> # Check if the dnscache tools are working:
# a) send a query to a DNS server somewhere at the Internet
dnsq a [www.google.com](www.google.com) 192.203.230.10
# b) send a query to an upstream DNS cache
env DNSCACHEIP=208.67.222.222 dnsqr a [www.google.com](www.google.com)

After entering "dnsq a [www.google.com](www.google.com) 192.203.230.10" at first nothing happens. After one minuit
```
1 www.google.com:
timed out

```
appears.

When I enter the command env DNSCACHEIP=208.67.222.222 dnsqr a [www.google.com](www.google.com), the terminal repeats:
```
1 www.google.com:
timed out
```

I'm using a Proxyserver. Could that be the problem?

In the last week I tried serveral good guides for DJBDNS. Every time there appeared a Problem at that test.

Is anyone able to help me?


Best greetings

Jan

---

