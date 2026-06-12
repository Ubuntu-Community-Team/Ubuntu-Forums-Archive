---
title: "dhcp3-server not working after dnsmasq uninstall"
date: 2010-03-24
forum: Server Platforms
---

### Post by BarryDocks on 2010-03-24
Hi there, 

hopefully someone can help, I have been trying to set up a DNS server and tried DNSMASQ but was not impressed so uninstalled it.  Before that I had a working DHCP3-server that now does not serve subnets.  If I manually set up clients I can connect ok.  

Any suggestions? (I am considering a complete reinstall of the OS)

---

### Post by Iowan on 2010-03-24
Personally, I like DNSMasq - but you're entitled to your opinion, too. Is the daemon running - or have the rcX.d links been overwritten/removed? (Does the server use upstart?)
Re-installing dhcp3-server might be adequate...

---

### Post by BarryDocks on 2010-03-25
I have, as far as I am aware, completely removed DNSMASQ (used atp-get autoremove --purge dnsmasq).  I have also removed and re-installed hdcp3-server but still no luck.

Not using upstart.  Could you point me in the direction of which rcX.d links to look at?

Thanks

---

### Post by Iowan on 2010-03-25
> **BarryDocks said:**
>  I have also removed and re-installed hdcp3-server but still no luck.Hmmm... I'd have thought a re-installation would have configured itself to start up... :(

---

### Post by BarryDocks on 2010-03-26
interestingly I get this repeatedly in the daemon log:
```
Mar 23 03:22:44 Server64 nmbd[6008]: [2010/03/23 03:22:44, 0] nmbd/nmbd.c:reload_interfaces(240) 
Mar 23 03:22:44 Server64 nmbd[6008]:   reload_interfaces: No sub
```
the dhcpd daemon is running but not serving any subnets.  Have also tried a reboot but still no luck](*,)

---

### Post by BarryDocks on 2010-03-26
Also if I remove dhcp3-server and then reinstall it I get the following:
```
> apt-get -fy install dhcp3-server
Reading package lists...
Building dependency tree...
Reading state information...
The following NEW packages will be installed
  dhcp3-server
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
dpkg-preconfigure: unable to re-open stdin: 
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/342kB of archives.
After this operation, 827kB of additional disk space will be used.
Selecting previously deselected package dhcp3-server.
(Reading database ... 49849 files and directories currently installed.)
Unpacking dhcp3-server (from .../dhcp3-server_3.0.6.dfsg-1ubuntu9.1_amd64.deb) ...
Setting up dhcp3-server (3.0.6.dfsg-1ubuntu9.1) ...
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
Generating /etc/default/dhcp3-server...
 * Starting DHCP server dhcpd3
   ...fail!
invoke-rc.d: initscript dhcp3-server, action "start" failed.

```
The server starts after I configure the dhcpd.conf file correctly but still no subnets!  Not sure what the debconf warnings are all about?

---

### Post by BarryDocks on 2010-04-05
managed to fix this, no idea how it works but used the following commands:

```
1. Install debsums 
sudo apt-get install debsums 

2. Create missing debsums 
cd /var/cache/apt/archives 
sudo apt-get --download-only --reinstall install `debsums -l` 
sudo debsums --generate=keep,nocheck *.deb 

3. Repair manipulated packages 
sudo debsums -c 2> /tmp/broken.log 
sed -n 's/^.*checksum mismatch \([^ ]*\) file.*$/\1/p;s/^.*t open \([^ ]*\) file.*$/\1/p' < /tmp/broken.log | sort -u > /tmp/broken.pkgs 
echo "Manipulated packages:" 
cat /tmp/broken.pkgs 
sudo apt-get --reinstall install `cat /tmp/broken.pkgs`
```

From: [http://brainstorm.ubuntu.com/idea/7770]("http://brainstorm.ubuntu.com/idea/7770")

---

