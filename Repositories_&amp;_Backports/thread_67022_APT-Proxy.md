---
title: "APT-Proxy"
date: 2005-09-19
forum: Repositories &amp; Backports
---

### Post by Brad wilkinson on 2005-09-19
Trying to set up APT-Proxy for my home pc's. I have a router (192.168.1.254) and 3 pc's (192.168.1.100, 110 and 111). so far I have installed the apt-proxy, but now I am having trouble setting up the sources.list and the apt-proxy-v2.conf files.

On the pc I want to use for the apt-proxy (damia, 192.168.1.100) I have the following

sources.list
> 
## Uncomment the following two lines to fetch updated software from the network
# deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://[COLOR=Red]192.168.1.100:9999](http://[COLOR=Red]192.168.1.100:9999)[/COLOR]/ubuntu hoary-updates main restricted universe
# deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://[COLOR=Red]192.168.1.100:9999](http://[COLOR=Red]192.168.1.100:9999)[/COLOR]/ubuntu hoary universe main restricted
# deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) hoary universe

# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://[COLOR=Red]192.168.1.100:9999](http://[COLOR=Red]192.168.1.100:9999)[/COLOR]/ubuntu hoary-security universe main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe


apt-proxy-v2.conf
> [DEFAULT]
;; All times are in seconds, but you can add a suffix
;; for minutes(m), hours(h) or days(d)

;; Server IP to listen on
address =[COLOR=Red] 192.168.1.254[/COLOR]

;; Server port to listen on
port =[COLOR=Red] 9999[/COLOR]

;; Control files (Packages/Sources/Contents) refresh rate
;;
;; Minimum time between attempts to refresh a file
min_refresh_delay = 1h

;; Minimum age of a file before attempting an update (NOT YET IMPLEMENTED)
;min_age = 23h

;; Uncomment to make apt-proxy continue downloading even if all
;; clients disconnect.  This is probably not a good idea on a
;; dial up line.
;; complete_clientless_downloads = 1

;; Debugging settings.
;; for all debug information use this:
;; debug = all:9
debug = all:4 db:0

;; Debugging remote python console
;; Do not enable in an untrusted environment
;telnet_port = 9998
;telnet_user = apt-proxy
;telnet_password = secret

;; Network timeout when retrieving from backend servers
timeout = 60

;; Cache directory for apt-proxy
cache_dir = /var/cache/apt-proxy

;; Use passive FTP? (default=on)
;passive_ftp = on

;; Use HTTP proxy?
;http_proxy = host:port

;; Enable HTTP pipelining within apt-proxy (for test purposes)
;disable_pipelining=0

;;--------------------------------------------------------------
;; Cache housekeeping

;; Time to perform periodic housekeeping:
;;  - delete files that have not been accessed in max_age
;;  - scan cache directories and update internal tables
cleanup_freq = 1d

;; Maximum age of files before deletion from the cache (seconds)
max_age = 120d

;; Maximum number of versions of a .deb to keep per distribution
max_versions = 3

;; Add HTTP backends dynamicaly if not already defined? (default=on)
;dynamic_backends = on

;;---------------------------------------------------------------
;;---------------------------------------------------------------
;; Backend servers
;;
;; Place each server in its own [section]

;;[debian]
;; The main Debian archive
;; You can override the default timeout like this:
;timeout = 30

;; Rsync server used to rsync the Packages file (NOT YET IMPLEMENTED)
;;rsyncpackages = rsync://ftp.de.debian.org/debian

;; Backend servers, in order of preference
;;backends = 
;;	[http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian)
;;	[http://ftp.de.debian.org/debian](http://ftp.de.debian.org/debian)
;;	[http://ftp2.de.debian.org/debian](http://ftp2.de.debian.org/debian)
;;	[ftp://ftp.uk.debian.org/debian](ftp://ftp.uk.debian.org/debian)


;;[debian-non-US]
;; Debian debian-non-US archive
;;timeout will be the global value
;;backends =
;;	[http://ftp.uk.debian.org/debian-non-US](http://ftp.uk.debian.org/debian-non-US)
;;	[http://ftp.de.debian.org/debian-non-US](http://ftp.de.debian.org/debian-non-US)
;;	[ftp://ftp.uk.debian.org/debian](ftp://ftp.uk.debian.org/debian)
	
;;[security]
;; Debian security archive
;;backends = 
;;	[http://security.debian.org/debian-security](http://security.debian.org/debian-security)
;;	[http://ftp2.de.debian.org/debian-security](http://ftp2.de.debian.org/debian-security)

[ubuntu]
;; Ubuntu archive
backends = [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu)

[ubuntu-security]
;; Ubuntu security updates
backends = [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)

[openoffice]
;; OpenOffice.org packages
backends =
	[http://ftp.freenet.de/pub/debian-openoffice](http://ftp.freenet.de/pub/debian-openoffice)
	[http://ftp.sh.cvut.cz/MIRRORS/OpenOffice.deb](http://ftp.sh.cvut.cz/MIRRORS/OpenOffice.deb)
	[http://borft.student.utwente.nl/debian](http://borft.student.utwente.nl/debian)
	
[apt-proxy]
;; Apt-proxy new versions
backends = [http://apt-proxy.sourceforge.net/apt-proxy](http://apt-proxy.sourceforge.net/apt-proxy)

;[backports.org]
;; backports.org
;backends = [http://backports.org/debian](http://backports.org/debian)

;[blackdown]
;; Blackdown Java
;backends = [http://ftp.gwdg.de/pub/languages/java/linux/debian](http://ftp.gwdg.de/pub/languages/java/linux/debian)


;[debian-people]
;; people.debian.org
;backends = [http://people.debian.org](http://people.debian.org)

;[emdebian]
;; The Emdebian project
;backends = [http://emdebian.sourceforge.net/emdebian](http://emdebian.sourceforge.net/emdebian)

;[rsync]
;; An example using an rsync server.  This is not recommended
;; unless http is not available, becuause rsync is only more
;; efficient for transferring uncompressed files and puts much
;; more overhead on the server.  See the rsyncpacakges parameter 
;; for a way of rsyncing just the Packages files.
;backends = rsync://ftp.uk.debian.org/debian


but when I try to apt-get update i get lots of errors
> brad@damia:~$ sudo apt-get update
Err [http://192.168.1.100](http://192.168.1.100) hoary-updates Release.gpg
  Could not connect to 192.168.1.100:9999 (192.168.1.100). - connect (111 Connection refused)
Err [http://192.168.1.100](http://192.168.1.100) hoary Release.gpg
  Could not connect to 192.168.1.100:9999 (192.168.1.100). - connect (111 Connection refused)
Err [http://192.168.1.100](http://192.168.1.100) hoary-security Release.gpg
  Could not connect to 192.168.1.100:9999 (192.168.1.100). - connect (111 Connection refused)
Ign [http://192.168.1.100](http://192.168.1.100) hoary-updates Release
Ign [http://192.168.1.100](http://192.168.1.100) hoary Release
Ign [http://192.168.1.100](http://192.168.1.100) hoary-security Release
Ign [http://192.168.1.100](http://192.168.1.100) hoary-updates/main Packages
Ign [http://192.168.1.100](http://192.168.1.100) hoary-updates/restricted Packages
Ign [http://192.168.1.100](http://192.168.1.100) hoary-updates/universe Packages
Ign [http://192.168.1.100](http://192.168.1.100) hoary/universe Packages
Ign [http://192.168.1.100](http://192.168.1.100) hoary/main Packages
Ign [http://192.168.1.100](http://192.168.1.100) hoary/restricted Packages
Ign [http://192.168.1.100](http://192.168.1.100) hoary-security/universe Packages
Ign [http://192.168.1.100](http://192.168.1.100) hoary-security/main Packages
Ign [http://192.168.1.100](http://192.168.1.100) hoary-security/restricted Packages
Err [http://192.168.1.100](http://192.168.1.100) hoary-updates/main Packages
  Could not connect to 192.168.1.100:9999 (192.168.1.100). - connect (111 Connection refused)
Err [http://192.168.1.100](http://192.168.1.100) hoary-updates/restricted Packages
  Could not connect to 192.168.1.100:9999 (192.168.1.100). - connect (111 Connection refused)
Err [http://192.168.1.100](http://192.168.1.100) hoary-updates/universe Packages
  Could not connect to 192.168.1.100:9999 (192.168.1.100). - connect (111 Connection refused)
Err [http://192.168.1.100](http://192.168.1.100) hoary/universe Packages
  Could not connect to 192.168.1.100:9999 (192.168.1.100). - connect (111 Connection refused)
Err [http://192.168.1.100](http://192.168.1.100) hoary/main Packages
  Could not connect to 192.168.1.100:9999 (192.168.1.100). - connect (111 Connection refused)
Err [http://192.168.1.100](http://192.168.1.100) hoary/restricted Packages
  Could not connect to 192.168.1.100:9999 (192.168.1.100). - connect (111 Connection refused)
Err [http://192.168.1.100](http://192.168.1.100) hoary-security/universe Packages
  Could not connect to 192.168.1.100:9999 (192.168.1.100). - connect (111 Connection refused)
Err [http://192.168.1.100](http://192.168.1.100) hoary-security/main Packages
  Could not connect to 192.168.1.100:9999 (192.168.1.100). - connect (111 Connection refused)
Err [http://192.168.1.100](http://192.168.1.100) hoary-security/restricted Packages
  Could not connect to 192.168.1.100:9999 (192.168.1.100). - connect (111 Connection refused)
Failed to fetch [http://192.168.1.100:9999/ubuntu/dists/hoary-updates/Release.gpg](http://192.168.1.100:9999/ubuntu/dists/hoary-updates/Release.gpg)  Could not connect to 192.168.1.100:9999 (192.168.1.100). - connect (111 Connection refused)
Failed to fetch [http://192.168.1.100:9999/ubuntu/dists/hoary/Release.gpg](http://192.168.1.100:9999/ubuntu/dists/hoary/Release.gpg)  Could not connect to 192.168.1.100:9999 (192.168.1.100). - connect (111 Connection refused)
Failed to fetch [http://192.168.1.100:9999/ubuntu/dists/hoary-security/Release.gpg](http://192.168.1.100:9999/ubuntu/dists/hoary-security/Release.gpg)  Could not connect to 192.168.1.100:9999 (192.168.1.100). - connect (111 Connection refused)
Failed to fetch [http://192.168.1.100:9999/ubuntu/dists/hoary-updates/main/binary-i386/Packages.gz](http://192.168.1.100:9999/ubuntu/dists/hoary-updates/main/binary-i386/Packages.gz)  Could not connect to 192.168.1.100:9999 (192.168.1.100). - connect (111 Connection refused)
Failed to fetch [http://192.168.1.100:9999/ubuntu/dists/hoary-updates/restricted/binary-i386/Packages.gz](http://192.168.1.100:9999/ubuntu/dists/hoary-updates/restricted/binary-i386/Packages.gz)  Could not connect to 192.168.1.100:9999 (192.168.1.100). - connect (111 Connection refused)
Failed to fetch [http://192.168.1.100:9999/ubuntu/dists/hoary-updates/universe/binary-i386/Packages.gz](http://192.168.1.100:9999/ubuntu/dists/hoary-updates/universe/binary-i386/Packages.gz)  Could not connect to 192.168.1.100:9999 (192.168.1.100). - connect (111 Connection refused)
Failed to fetch [http://192.168.1.100:9999/ubuntu/dists/hoary/universe/binary-i386/Packages.gz](http://192.168.1.100:9999/ubuntu/dists/hoary/universe/binary-i386/Packages.gz)  Could not connect to 192.168.1.100:9999 (192.168.1.100). - connect (111 Connection refused)
Failed to fetch [http://192.168.1.100:9999/ubuntu/dists/hoary/main/binary-i386/Packages.gz](http://192.168.1.100:9999/ubuntu/dists/hoary/main/binary-i386/Packages.gz)  Could not connect to 192.168.1.100:9999 (192.168.1.100). - connect (111 Connection refused)
Failed to fetch [http://192.168.1.100:9999/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz](http://192.168.1.100:9999/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz)  Could not connect to 192.168.1.100:9999 (192.168.1.100). - connect (111 Connection refused)
Failed to fetch [http://192.168.1.100:9999/ubuntu/dists/hoary-security/universe/binary-i386/Packages.gz](http://192.168.1.100:9999/ubuntu/dists/hoary-security/universe/binary-i386/Packages.gz)  Could not connect to 192.168.1.100:9999 (192.168.1.100). - connect (111 Connection refused)
Failed to fetch [http://192.168.1.100:9999/ubuntu/dists/hoary-security/main/binary-i386/Packages.gz](http://192.168.1.100:9999/ubuntu/dists/hoary-security/main/binary-i386/Packages.gz)  Could not connect to 192.168.1.100:9999 (192.168.1.100). - connect (111 Connection refused)
Failed to fetch [http://192.168.1.100:9999/ubuntu/dists/hoary-security/restricted/binary-i386/Packages.gz](http://192.168.1.100:9999/ubuntu/dists/hoary-security/restricted/binary-i386/Packages.gz)  Could not connect to 192.168.1.100:9999 (192.168.1.100). - connect (111 Connection refused)
Reading package lists... Done
W: Couldn't stat source package list [http://192.168.1.100](http://192.168.1.100) hoary-updates/main Packages (/var/lib/apt/lists/192.168.1.100:9999_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://192.168.1.100](http://192.168.1.100) hoary-updates/restricted Packages (/var/lib/apt/lists/192.168.1.100:9999_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://192.168.1.100](http://192.168.1.100) hoary-updates/universe Packages (/var/lib/apt/lists/192.168.1.100:9999_ubuntu_dists_hoary-updates_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://192.168.1.100](http://192.168.1.100) hoary/universe Packages (/var/lib/apt/lists/192.168.1.100:9999_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://192.168.1.100](http://192.168.1.100) hoary/main Packages (/var/lib/apt/lists/192.168.1.100:9999_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://192.168.1.100](http://192.168.1.100) hoary/restricted Packages (/var/lib/apt/lists/192.168.1.100:9999_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://192.168.1.100](http://192.168.1.100) hoary-security/universe Packages (/var/lib/apt/lists/192.168.1.100:9999_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://192.168.1.100](http://192.168.1.100) hoary-security/main Packages (/var/lib/apt/lists/192.168.1.100:9999_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://192.168.1.100](http://192.168.1.100) hoary-security/restricted Packages (/var/lib/apt/lists/192.168.1.100:9999_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


and I get similar errors when I try to do apt-get update from either of the other 2 pc's that should be going through the apt-proxy.

I've been using the howto from the wiki, and i've been and found the debian howto as well, but I still cannot figure it out properly. Can someone show me how to set the lines above[COLOR=Red] (in red)[/COLOR] so it will work properly please?

I know this is a very long post, but I need help (yes yes, I have a therapist as well....)

Also, could host.allow and host.deny have something to do with this working or not? Ive read the man pages and looked at them, but newb-itis strikes again.... ](*,) :?

---

### Post by lithorus on 2005-09-19
> address = 192.168.1.254
It shouldn't really listen on 254, but 100.

---

### Post by Glut on 2005-09-19
Just to add a little explanation to that,
Your address line is telling it to listen on the network interface that has the ip address 192.168.0.254
The address assigned to your main interface (probably eth0) is .100

So it's tried to open a port on the .254 interface and probably failed, because I'm guessing  .254 is your router rather than the proxy machine.
So when the other machines look at the .100 machine, the port 9999 is not open. If you change that line to the read 100, apt-proxy will open a port on the .100 interface and the other machines will be able to see it.

---

### Post by Brad wilkinson on 2005-09-20
thanks fellas

---

### Post by daller on 2006-09-30
O.k. this thread is old, but I'll try anyway!

I have a somewhat similar problem:

Apt-proxy works on the local machine (localhost:9999)

But if I try connecting from another machine, it fails! (192.168.0.111:9999, which is the IP of the apt-proxy machine!)

**Connection Refused**

How do I fix that? (I'm on Edgy (Both server and client! - And have tried a client on Dapper too!), if that's any difference?)

**Edit: Can it be a firewall-problem with my router? - And if so, any ideas on how to fix it? (D-Link DI-514)**

---

### Post by crazymonkey on 2006-10-22
Are your client and server on the same side of the firewall/router? If not you might have to set port forwarding.

You should also make sure that your config is set to listen on your localhost AND network.

> ;; Server IP to listen on
address = 192.168.1.111
address = localhost

---

