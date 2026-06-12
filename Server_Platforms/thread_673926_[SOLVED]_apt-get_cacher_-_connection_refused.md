---
title: "[SOLVED] apt-get cacher - connection refused"
date: 2008-01-21
forum: Server Platforms
---

### Post by depele on 2008-01-21
hello, 

I have multiple computers running Ubuntu gutsy.

I have one server running Ubuntu feisty.

On the server I installed apt-cacher and configured it following this guide. [http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher-p2](http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher-p2)

I think the basics are working.
Can somebody help me avoiding these errors.

apt-cacher.conf
```
path_map = debuntu repository.debuntu.org ; ubuntu be.archive.ubuntu.com/ubuntu; ubuntu-updates be.archive.ubuntu.com/ubuntu ; ubuntu-security security.ubuntu.com/ubuntu ; canoncial archive.canonical.com/ubuntu ; avant download.tuxfamily.org/syzygy42

```

sources.list on gutsy laptop
```
#debuntu repository
deb http://server:3142/debuntu gutsy multiverse
deb-src http://server:3142/debuntu gutsy multiverse

#ubuntu main repository
deb http://server:3142/ubuntu gutsy gutsy-backports main restricted universe multiverse
deb-src http://server:3142/ubuntu gutsy gutsy-backports main restricted universe multiverse

#ubuntu updates repository
deb http://server:3142/ubuntu-updates gutsy-updates main restricted universe multiverse
deb-src http://server:3142/ubuntu-updates gutsy-updates main restricted universe multiverse

#ubuntu security updates repository
deb http://server:3142/ubuntu-security gutsy-security main restricted universe multiverse
deb-src http://server:3142/ubuntu-security gutsy-security main restricted universe multiverse

#cononcial

deb http://server:3124/canoncial gutsy partner
#deb-src http:///server:3124/canoncial gutsy partner


#awn manager
deb http://server:3124/avant gusty avant-window-navigator
deb-src http://server:3124/avant gusty avant-window-navigator
```

I get this errors from synaptic
```
http://server:3124/canoncial/dists/gutsy/Release.gpg: Could not connect to server:3124 (192.168.1.2). - connect (111 Connection refused)
http://server:3124/canoncial/dists/gutsy/partner/i18n/Translation-en_US.bz2: Could not connect to server:3124 (192.168.1.2). - connect (111 Connection refused)
http://server:3124/avant/dists/gusty/Release.gpg: Could not connect to server:3124 (192.168.1.2). - connect (111 Connection refused)
http://server:3124/avant/dists/gusty/avant-window-navigator/i18n/Translation-en_US.bz2: Could not connect to server:3124 (192.168.1.2). - connect (111 Connection refused)
http://server:3142/ubuntu/dists/gutsy/Release: Unable to find expected entry  gutsy-backports/binary-i386/Packages in Meta-index file (malformed Release file?)

```

and

```
W: GPG error: http://server gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0E466170BCF1FC29
```

command line errors: (I know it is the same)

```
sudo aptitude update
Get:1 http://server gutsy Release.gpg [189B]
Ign http://server gutsy/multiverse Translation-en_US
Get:2 http://server gutsy Release.gpg [191B]
Ign http://server gutsy/gutsy-backports Translation-en_US
Ign http://server gutsy/main Translation-en_US
Ign http://server gutsy/restricted Translation-en_US
Ign http://server gutsy/universe Translation-en_US
Ign http://server gutsy/multiverse Translation-en_US
Get:3 http://server gutsy-updates Release.gpg [191B]
Ign http://server gutsy-updates/main Translation-en_US
Ign http://server gutsy-updates/restricted Translation-en_US
Ign http://server gutsy-updates/universe Translation-en_US
Ign http://server gutsy-updates/multiverse Translation-en_US
Get:4 http://server gutsy-security Release.gpg [191B]
Ign http://server gutsy-security/main Translation-en_US
Ign http://server gutsy-security/restricted Translation-en_US
Ign http://server gutsy-security/universe Translation-en_US
Ign http://server gutsy-security/multiverse Translation-en_US
Err http://server gutsy Release.gpg
  Could not connect to server:3124 (192.168.1.2). - connect (111 Connection refused)
Err http://server gutsy/partner Translation-en_US
  Could not connect to server:3124 (192.168.1.2). - connect (111 Connection refused)
Err http://server gusty Release.gpg     
  Could not connect to server:3124 (192.168.1.2). - connect (111 Connection refused)
Err http://server gusty/avant-window-navigator Translation-en_US
  Could not connect to server:3124 (192.168.1.2). - connect (111 Connection refused)
Get:5 http://server gutsy Release [3070B]
Ign http://server gutsy Release                                                                                                                             
Get:6 http://server gutsy Release [65.9kB]                                                                                                                  
Get:7 http://server gutsy-updates Release [58.5kB]                                                                                                          
Get:8 http://server gutsy-security Release [51.2kB]                                                                                                         
Get:9 http://server gutsy/multiverse Packages [4685B]                                                                                                       
Get:10 http://server gutsy/multiverse Sources [1519B]                                                                                                       
Get:11 http://server gutsy-updates/main Packages [126kB]                                                                                                    
Get:12 http://server gutsy-updates/restricted Packages [4263B]                                                                                              
Get:13 http://server gutsy-updates/universe Packages [50.0kB]                                                                                               
Get:14 http://server gutsy-updates/multiverse Packages [9215B]                                                                                              
Get:15 http://server gutsy-updates/main Sources [30.4kB]                                                                                                    
Get:16 http://server gutsy-updates/restricted Sources [937B]                                                                                                
Get:17 http://server gutsy-updates/universe Sources [8412B]                                                                                                 
Get:18 http://server gutsy-updates/multiverse Sources [1702B]                                                                                               
Get:19 http://server gutsy-security/main Packages [66.1kB]                                                                                                  
Get:20 http://server gutsy-security/restricted Packages [14B]                                                                                               
Get:21 http://server gutsy-security/universe Packages [36.7kB]                                                                                              
Get:22 http://server gutsy-security/multiverse Packages [2903B]                                                                                             
Get:23 http://server gutsy-security/main Sources [11.8kB]                                                                                                   
Get:24 http://server gutsy-security/restricted Sources [14B]                                                                                                
Get:25 http://server gutsy-security/universe Sources [4731B]                                                                                                
Get:26 http://server gutsy-security/multiverse Sources [833B]                                                                                               
Fetched 540kB in 18s (29.8kB/s)                                                                                                                             
W: GPG error: http://server gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0E466170BCF1FC29
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Couldn't rebuild package cache
```

---

### Post by depele on 2008-01-22
*daily bump*

---

### Post by depele on 2008-01-23
*daily bump*

---

### Post by depele on 2008-01-23
*evening bump*

---

### Post by depele on 2008-01-24
please anyone? do you need more information?

---

### Post by depele on 2008-01-26
Ok, I went searching for help elsewhere.

Here is the sollution.

I had to change some things on the sources.list.

I also had some writing errors.


As attachment my Sources.list

---

