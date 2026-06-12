---
title: "Failed to fetch - using apt-get update - error 111"
date: 2013-04-15
forum: Server Platforms
---

### Post by Hexxus on 2013-04-15
Hello,

I've done some searching and all of the results I found are related to DNS lookup issues that people had with external hostnames.

My problem is that my server cannot download updates.

It can Resolve external hostnames
It can ping any address (inside network, outside network) 
Is NOT behind a proxy (like anon-proxy) 
No firewall blockages 
Correct DNS servers (Using googles 8.8.8.8 for testing)


Here is the error report:

```
Err http://security.ubuntu.com lucid-security Release.gpg
  Could not connect to security.ubuntu.com:80 (91.189.91.13). - connect (111: Connection refused) [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.91.13 80]
Err http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.91.13 80]
Err http://ppa.launchpad.net lucid Release.gpg                            
  Could not connect to ppa.launchpad.net:80 (91.189.95.83). - connect (111: Connection refused)
Err http://ppa.launchpad.net/txwikinger/php5.2/ubuntu/ lucid/main Translation-en_US
  Unable to connect to ppa.launchpad.net:http:
Err http://us.archive.ubuntu.com lucid Release.gpg                        
  Could not connect to us.archive.ubuntu.com:80 (91.189.91.14). - connect (111: Connection refused) [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com lucid-updates Release.gpg
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Err http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]
Reading package lists... Done
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg  Could not connect to us.archive.ubuntu.com:80 (91.189.91.14). - connect (111: Connection refused) [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.14 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg  Could not connect to security.ubuntu.com:80 (91.189.91.13). - connect (111: Connection refused) [IP: 91.189.91.13 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2  Unable to connect to security.ubuntu.com:http: [IP: 91.189.91.13 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2  Unable to connect to security.ubuntu.com:http: [IP: 91.189.91.13 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2  Unable to connect to security.ubuntu.com:http: [IP: 91.189.91.13 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2  Unable to connect to security.ubuntu.com:http: [IP: 91.189.91.13 80]

W: Failed to fetch http://ppa.launchpad.net/txwikinger/php5.2/ubuntu/dists/lucid/Release.gpg  Could not connect to ppa.launchpad.net:80 (91.189.95.83). - connect (111: Connection refused)

W: Failed to fetch http://ppa.launchpad.net/txwikinger/php5.2/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2  Unable to connect to ppa.launchpad.net:http:

W: Some index files failed to download, they have been ignored, or old ones used instead.



```

Any thoughts? 

Thanks guys!

---

### Post by Hexxus on 2013-04-15
Scratch that - there was a firewall policy blocking traffic from that host... Sorry everyone!

---

