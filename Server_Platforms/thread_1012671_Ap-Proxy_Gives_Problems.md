---
title: "Ap-Proxy Gives Problems"
date: 2008-12-16
forum: Server Platforms
---

### Post by shoaibi on 2008-12-16
Following Code section contains all what i think i have to offer...

```



root@aptproxy:~# /etc/init.d/apt-proxy restart
 * Stopping apt-proxy                                                                                                                                 [ OK ] 
 * Starting apt-proxy                                                                                                                                        /usr/lib/python2.5/site-packages/twisted/manhole/telnet.py:8: DeprecationWarning: As of Twisted 2.1, twisted.protocols.telnet is deprecated.  See twisted.conch.telnet for the current, supported API.
  from twisted.protocols import telnet
None
/usr/lib/python2.5/site-packages/twisted/manhole/telnet.py:8: DeprecationWarning: As of Twisted 2.1, twisted.protocols.telnet is deprecated.  See twisted.conch.telnet for the current, supported API.
  from twisted.protocols import telnet
None


root@aptproxy:/etc/apt# cat sources.list
#
#  /etc/apt/sources.list
#


#
# intrepid
#
deb     http://aptproxy:9999/ubuntu     intrepid main restricted universe multiverse
deb-src http://aptproxy:9999/ubuntu     intrepid main restricted universe
deb     http://aptproxy:9999/ubuntu     intrepid-updates main restricted universe multiverse
deb-src http://aptproxy:9999/ubuntu     intrepid-updates main restricted universe
deb http://aptproxy:9999/ubuntu intrepid-security main restricted universe
deb-src http://aptproxy:9999/ubuntu intrepid-security main restricted universe




root@aptproxy:/etc/apt# cat /etc/apt-proxy/apt-proxy-v2.conf
[DEFAULT]
;; All times are in seconds, but you can add a suffix
;; for minutes(m), hours(h) or days(d)

;; Server IP to listen on
address = 192.168.30.21

;; Server port to listen on
port = 9999

;; Control files (Packages/Sources/Contents) refresh rate
;;
;; Minimum age of a file before it is refreshed
min_refresh_delay = 1h

;; Minimum age of a file before attempting an update (NOT YET IMPLEMENTED)
;min_age = 23h

;; Uncomment to make apt-proxy continue downloading even if all
;; clients disconnect.  This is probably not a good idea on a
;; dial up line.
complete_clientless_downloads = 1

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
timeout = 15

;; Cache directory for apt-proxy
cache_dir = /var/cache/apt-proxy

;; Use passive FTP? (default=on)
passive_ftp = on

;; Use HTTP proxy?
;http_proxy = [username:password@]host:port

;; Limit download rate from backend servers (http and rsync only), in bytes/sec
;bandwidth_limit = 100000

;;--------------------------------------------------------------
;; Cache housekeeping

;; Time to perform periodic housekeeping:
;;  - delete files that have not been accessed in max_age
;;  - scan cache directories and update internal tables
cleanup_freq = 1d

;; Maximum age of files before deletion from the cache (seconds)
max_age = 30d

;; Maximum number of versions of a .deb to keep per distribution
max_versions = 3

;; Add HTTP backends dynamicaly if not already defined? (default=on)
dynamic_backends = on

;;---------------------------------------------------------------
;;---------------------------------------------------------------
;; Backend servers
;;
;; Place each server in its own [section]

[ubuntu]
;; Ubuntu archive
backends = http://archive.ubuntu.com/ubuntu
min_refresh_delay = 15m

[ubuntu-security]
;; Ubuntu security updates
backends = http://security.ubuntu.com/ubuntu
min_refresh_delay = 1m

[openoffice-3]
;; Open Office v3 for ubuntu
backends = http://ppa.launchpad.net/openoffice-pkgs/ubuntu

[kubuntu-members-kde]
;; KDE 4 respository.
backends = http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu
min_refresh_delay = 1m

[virtualbox]
;; Virtualbox Repository
backends = http://download.virtualbox.org/virtualbox/debian
min_refresh_delay = 1m

[canonical]
;; Partner Repository
backends = http://archive.canonical.com/ubuntu 
min_refresh_delay = 1m


;[backports.org]
;; backports.org
;backends = http://backports.org/debian
min_refresh_delay = 1d

;[blackdown]
;; Blackdown Java
;backends = http://ftp.gwdg.de/pub/languages/java/linux/debian
min_refresh_delay = 1d

;[debian-people]
;; people.debian.org
;backends = http://people.debian.org

;[emdebian]
;; The Emdebian project
;backends = http://emdebian.sourceforge.net/emdebian

;[rsync]
;; An example using an rsync server.  This is not recommended
;; unless http is not available, becuause rsync is only more
;; efficient for transferring uncompressed files and puts much
;; more overhead on the server.
;backends = rsync://ftp.uk.debian.org/debian



root@aptproxy:/etc/apt# apt-get update
Err http://aptproxy intrepid Release.gpg
  Connection failed
Err http://aptproxy intrepid-updates Release.gpg
  Connection failed
Err http://aptproxy intrepid-security Release.gpg
  Connection failed
Ign http://aptproxy intrepid Release       
Ign http://aptproxy intrepid-updates Release
5% [Waiting for headers]  


```


meanwhile apt-proxy.log shows:

```

2008-12-16 14:10:00+0500 [Channel,3,192.168.40.51] [CacheEntry] this is a real request:/var/cache/apt-proxy/ubuntu/dists/intrepid/Release.gpg
2008-12-16 14:10:00+0500 [Channel,3,192.168.40.51] [CacheEntry] start download:dists/intrepid/Release.gpg
2008-12-16 14:10:00+0500 [Channel,3,192.168.40.51] [CacheEntry] this is a real request:/var/cache/apt-proxy/ubuntu/dists/intrepid-updates/Release.gpg
2008-12-16 14:10:00+0500 [Channel,3,192.168.40.51] [CacheEntry] start download:dists/intrepid-updates/Release.gpg
2008-12-16 14:10:00+0500 [Channel,3,192.168.40.51] [CacheEntry] this is a real request:/var/cache/apt-proxy/ubuntu/dists/intrepid-security/Release.gpg
2008-12-16 14:10:00+0500 [Channel,3,192.168.40.51] [CacheEntry] start download:dists/intrepid-security/Release.gpg
2008-12-16 14:12:00+0500 [Channel,4,192.168.40.51] [CacheEntry] this is a real request:/var/cache/apt-proxy/ubuntu/dists/intrepid/Release.gpg
2008-12-16 14:12:00+0500 [Channel,4,192.168.40.51] [CacheEntry] start download:dists/intrepid/Release.gpg
2008-12-16 14:14:00+0500 [Channel,5,192.168.40.51] [CacheEntry] this is a real request:/var/cache/apt-proxy/ubuntu/dists/intrepid-updates/Release.gpg
2008-12-16 14:14:00+0500 [Channel,5,192.168.40.51] [CacheEntry] start download:dists/intrepid-updates/Release.gpg
2008-12-16 14:16:00+0500 [Channel,6,192.168.40.51] [CacheEntry] this is a real request:/var/cache/apt-proxy/ubuntu/dists/intrepid-updates/Release.gpg
2008-12-16 14:16:00+0500 [Channel,6,192.168.40.51] [CacheEntry] start download:dists/intrepid-updates/Release.gpg
2008-12-16 14:18:00+0500 [Channel,7,192.168.40.51] [CacheEntry] this is a real request:/var/cache/apt-proxy/ubuntu/dists/intrepid-security/Release.gpg
2008-12-16 14:18:00+0500 [Channel,7,192.168.40.51] [CacheEntry] start download:dists/intrepid-security/Release.gpg
2008-12-16 14:20:00+0500 [Channel,8,192.168.40.51] [CacheEntry] this is a real request:/var/cache/apt-proxy/ubuntu/dists/intrepid-security/Release.gpg
2008-12-16 14:20:00+0500 [Channel,8,192.168.40.51] [CacheEntry] start download:dists/intrepid-security/Release.gpg
2008-12-16 14:22:00+0500 [Channel,9,192.168.40.51] [CacheEntry] this is a real request:/var/cache/apt-proxy/ubuntu/dists/intrepid/Release
2008-12-16 14:22:00+0500 [Channel,9,192.168.40.51] [CacheEntry] start download:dists/intrepid/Release
2008-12-16 14:24:00+0500 [Channel,10,192.168.40.51] [CacheEntry] this is a real request:/var/cache/apt-proxy/ubuntu/dists/intrepid/Release
2008-12-16 14:24:00+0500 [Channel,10,192.168.40.51] [CacheEntry] start download:dists/intrepid/Release
2008-12-16 14:26:00+0500 [Channel,11,192.168.40.51] [CacheEntry] this is a real request:/var/cache/apt-proxy/ubuntu/dists/intrepid-updates/Release
2008-12-16 14:26:00+0500 [Channel,11,192.168.40.51] [CacheEntry] start download:dists/intrepid-updates/Release
2008-12-16 14:28:00+0500 [Channel,12,192.168.40.51] [CacheEntry] this is a real request:/var/cache/apt-proxy/ubuntu/dists/intrepid-updates/Release
2008-12-16 14:28:00+0500 [Channel,12,192.168.40.51] [CacheEntry] start download:dists/intrepid-updates/Release
2008-12-16 14:30:00+0500 [Channel,13,192.168.40.51] [CacheEntry] this is a real request:/var/cache/apt-proxy/ubuntu/dists/intrepid-security/Release
2008-12-16 14:30:00+0500 [Channel,13,192.168.40.51] [CacheEntry] start download:dists/intrepid-security/Release



```

and no one can update using this aptproxy server.

Its Ubuntu 8.10 Intrepid Ibex, fully upgraded.

---

