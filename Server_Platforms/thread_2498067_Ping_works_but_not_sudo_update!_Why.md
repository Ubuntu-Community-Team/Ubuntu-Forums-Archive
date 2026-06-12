---
title: "Ping works but not sudo update! Why?"
date: 2024-05-29
forum: Server Platforms
---

### Post by civilpolisen on 2024-05-29
```

civilpolisen@server:~$ sudo apt-get update 
Bra:1 http://se.archive.ubuntu.com/ubuntu xenial InRelease
Bra:2 http://se.archive.ubuntu.com/ubuntu xenial-updates InRelease                            
Bra:3 http://se.archive.ubuntu.com/ubuntu xenial-backports InRelease                              
Bra:4 http://ppa.launchpad.net/certbot/certbot/ubuntu xenial InRelease                            
Ign:5 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial InRelease                         
Ign:6 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial Release                           
Ign:7 http://nightly.odoo.com/10.0/nightly/deb ./ InRelease                                       
Ign:8 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main amd64 Packages               
Bra:9 http://nightly.odoo.com/10.0/nightly/deb ./ Release                                         
Ign:10 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main i386 Packages
Bra:11 http://security.ubuntu.com/ubuntu xenial-security InRelease        
Ign:12 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main all Packages
Ign:13 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main Translation-sv_SE
Ign:14 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main Translation-sv
Ign:15 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main Translation-en
Ign:8 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main amd64 Packages
Ign:10 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main i386 Packages
Ign:12 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main all Packages
Ign:13 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main Translation-sv_SE
Ign:14 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main Translation-sv
Ign:15 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main Translation-en
Ign:8 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main amd64 Packages
Ign:10 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main i386 Packages
Ign:12 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main all Packages
Ign:13 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main Translation-sv_SE
Ign:14 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main Translation-sv
Ign:15 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main Translation-en
Ign:8 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main amd64 Packages
Ign:10 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main i386 Packages
Ign:12 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main all Packages
Ign:13 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main Translation-sv_SE
Ign:14 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main Translation-sv
Ign:15 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main Translation-en
Ign:8 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main amd64 Packages
Ign:10 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main i386 Packages
Ign:12 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main all Packages
Ign:13 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main Translation-sv_SE
Ign:14 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main Translation-sv
Ign:15 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main Translation-en
Ign:8 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main amd64 Packages
Ign:10 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main i386 Packages
Ign:12 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main all Packages
Ign:13 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main Translation-sv_SE
Ign:14 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main Translation-sv
Ign:15 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main Translation-en
Fel:8 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main amd64 Packages
  404  Not Found [IP: 185.125.190.80 80]
Ign:10 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main i386 Packages
Ign:12 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main all Packages
Ign:13 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main Translation-sv_SE
Ign:14 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main Translation-sv
Ign:15 http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial/main Translation-en
Läser paketlistor… Färdig 
W: The repository 'http://ppa.launchpad.net/ferramroberto/lffl/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
civilpolisen@server:~$ ping ppa.launchpad.net
PING ppa.launchpad.net (185.125.190.80) 56(84) bytes of data.
64 bytes from ppa.launchpadcontent.net (185.125.190.80): icmp_seq=1 ttl=56 time=31.5 ms
64 bytes from ppa.launchpadcontent.net (185.125.190.80): icmp_seq=2 ttl=56 time=31.6 ms
64 bytes from ppa.launchpadcontent.net (185.125.190.80): icmp_seq=3 ttl=56 time=31.6 ms
64 bytes from ppa.launchpadcontent.net (185.125.190.80): icmp_seq=4 ttl=56 time=31.5 ms
64 bytes from ppa.launchpadcontent.net (185.125.190.80): icmp_seq=5 ttl=56 time=31.5 ms
64 bytes from ppa.launchpadcontent.net (185.125.190.80): icmp_seq=6 ttl=56 time=31.6 ms
64 bytes from ppa.launchpadcontent.net (185.125.190.80): icmp_seq=7 ttl=56 time=31.5 ms
64 bytes from ppa.launchpadcontent.net (185.125.190.80): icmp_seq=8 ttl=56 time=31.6 ms
64 bytes from ppa.launchpadcontent.net (185.125.190.80): icmp_seq=9 ttl=56 time=31.5 ms
64 bytes from ppa.launchpadcontent.net (185.125.190.80): icmp_seq=10 ttl=56 time=31.6 ms
64 bytes from ppa.launchpadcontent.net (185.125.190.80): icmp_seq=11 ttl=56 time=31.6 ms
64 bytes from ppa.launchpadcontent.net (185.125.190.80): icmp_seq=12 ttl=56 time=31.6 ms
^C
--- ppa.launchpad.net ping statistics ---
12 packets transmitted, 12 received, 0% packet loss, time 11009ms
rtt min/avg/max/mdev = 31.539/31.603/31.641/0.033 ms

```

The title and the enclosed log is fairly describing. How come ping is working but not sudo update? What am I missing!?

---

### Post by Rubi1200 on 2024-05-29
Unless you have extended support, Xenial support ended April 2021.

It also seems the PPA has not been updated. You could try contacting the author about this.

Time to backup and do a fresh install of a recent LTS release.

Or did I misunderstand something here?

---

