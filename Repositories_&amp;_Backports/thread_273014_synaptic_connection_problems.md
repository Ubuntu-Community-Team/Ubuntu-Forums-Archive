---
title: "synaptic connection problems"
date: 2006-10-07
forum: Repositories &amp; Backports
---

### Post by kolesarm on 2006-10-07
i have problems connecting to the online repositories.

i connect to the internet using automatic proxy configuration, but i dont know how to set up synaptic - the 'direct connection to the internet' option doesnt work - i get the following error:
[I]W: Couldn't stat source package list [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-updates/universe Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_breezy-updates_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) breezy-updates/multiverse Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_breezy-updates_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
[/I]

its similar when i try manual proxy

does anyone have any suggestions? it might be the way the network is set up - i'm on college network, and, say ```
ping www.ireland.com
``` spits out the following:
```
PING www.ireland.com (195.7.33.37) 56(84) bytes of data.
From 10.5.0.1 icmp_seq=2 Packet filtered
From 10.5.0.1 icmp_seq=16 Packet filtered
From 10.5.0.1 icmp_seq=20 Packet filtered
From 10.5.0.1 icmp_seq=28 Packet filtered
From 10.5.0.1 icmp_seq=31 Packet filtered
From 10.5.0.1 icmp_seq=33 Packet filtered
From 10.5.0.1 icmp_seq=34 Packet filtered

--- www.ireland.com ping statistics ---
35 packets transmitted, 0 received, +7 errors, 100% packet loss, time 34014ms


```

...

---

### Post by kolesarm on 2006-10-07
ok, i've made some progress since. it indeed appears to be an internet connection problem in that i need to authenticate myself at the proxy server first. 
however, i don't know how to set up synaptic so that i send my username and password to the server. 
the *wget* utility, for example, offers options *--proxy-user* and *--proxy-password* - is there anything similar available with synaptic/apt??

---

### Post by kolesarm on 2006-10-07
the answer already appeared in the forums - [http://www.ubuntuforums.org/showthread.php?t=210695&highlight=proxy+authentication+synaptic]("http://www.ubuntuforums.org/showthread.php?t=210695&highlight=proxy+authentication+synaptic")

now the problem is solved - i needed to insert

```
http_proxy=http://username:passwd@proxypac.tcd.ie/accelerated_pac_base.pac
export http_proxy
```

in the .bashrc file and now the apt-get is working!!

---

