---
title: "apt-get update fails"
date: 2011-02-16
forum: Server Platforms
---

### Post by josh.scott on 2011-02-16
For some reason I cannot apt-get update anymore. I am at a loss. I can ping the addresses just fine. Any help would be appreciated.

```
ping -c 3 us.archive.ubuntu.com
```
PING us.archive.ubuntu.com (91.189.92.169) 56(84) bytes of data.
64 bytes from caryopsis.canonical.com (91.189.92.169): icmp_seq=1 ttl=52 time=111 ms
64 bytes from caryopsis.canonical.com (91.189.92.169): icmp_seq=2 ttl=52 time=109 ms
64 bytes from caryopsis.canonical.com (91.189.92.169): icmp_seq=3 ttl=52 time=109 ms
--- us.archive.ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 109.061/109.830/111.178/0.993 ms

```
sudo apt-get update
```
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg
  Could not connect to ppa.launchpad.net:80 (91.189.90.217). - connect (111: Connection refused)
Err [http://ppa.launchpad.net/freenx-team/ppa/ubuntu/](http://ppa.launchpad.net/freenx-team/ppa/ubuntu/) lucid/main Translation-en_US
  Unable to connect to ppa.launchpad.net:http:
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
  Could not connect to security.ubuntu.com:80 (91.189.92.167). - connect (111: Connection refused) [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (91.189.92.169). - connect (111: Connection refused) [IP: 91.189.92.169 80]
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.169 80]
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.169 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.169 80]
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.169 80]
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.169 80]
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Could not connect to us.archive.ubuntu.com:80 (91.189.92.169). - connect (111: Connection refused) [IP: 91.189.92.169 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.169 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.169 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.169 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.169 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2)  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.92.169 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (91.189.92.167). - connect (111: Connection refused) [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://ppa.launchpad.net/freenx-team/ppa/ubuntu/dists/lucid/Release.gpg](http://ppa.launchpad.net/freenx-team/ppa/ubuntu/dists/lucid/Release.gpg)  Could not connect to ppa.launchpad.net:80 (91.189.90.217). - connect (111: Connection refused)

W: Failed to fetch [http://ppa.launchpad.net/freenx-team/ppa/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/freenx-team/ppa/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Unable to connect to ppa.launchpad.net:http:

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by James78 on 2011-02-16
This help?
[http://ubuntuforums.org/showpost.php?p=211780&postcount=3](http://ubuntuforums.org/showpost.php?p=211780&postcount=3)

---

### Post by josh.scott on 2011-02-16
Nope results still the same.

---

### Post by gmargo on 2011-02-16
Do you need to configure a proxy?  Or have you been experimenting with transparent proxying? Can you browse the web normally otherwise?

---

### Post by josh.scott on 2011-02-16
I haven't changed, modified, or tried to set up any proxy settings but when I tried to

```
link www.google.com
```

I got a connection refused as well.

I guess its possible that there is something different on the firewall. I'll look into that.

---

### Post by josh.scott on 2011-02-16
BAH! sys admin blocked port 80 outbound! Sorry everyone.

---

### Post by Vegan on 2011-02-16
port 80 is hppt, nice guy to block it.

my isp up here in Canada does not block anything

---

