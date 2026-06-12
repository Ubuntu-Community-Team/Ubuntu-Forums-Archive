---
title: "apt-get  connection refused"
date: 2010-11-01
forum: Server Platforms
---

### Post by pytheas22 on 2010-11-01
I have an Ubuntu 10.04 server (running as a virtual machine) on which "apt-get update" has mysteriously started failing with output like this:

```
# apt-get update
Err http://security.ubuntu.com lucid-security Release.gpg
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111: Connection refused) [IP: 91.189.88.37 80]
Err http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
Err http://archive.ubuntu.com lucid Release.gpg                        
  Could not connect to archive.ubuntu.com:80 (91.189.92.172). - connect (111: Connection refused) [IP: 91.189.92.172 80]
Err http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US     
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.172 80]
Err http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.172 80]
Err http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.172 80]
Err http://archive.ubuntu.com lucid-updates Release.gpg
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.172 80]
Err http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.172 80]
Err http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.172 80]
Err http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.172 80]
Err http://ppa.launchpad.net lucid Release.gpg
  Could not connect to ppa.launchpad.net:80 (91.189.90.217). - connect (111: Connection refused)
Err http://ppa.launchpad.net/likewise-open/likewise-open-ppa/ubuntu/ lucid/main Translation-en_US
  Unable to connect to ppa.launchpad.net:http:
Reading package lists... Done       
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg  Could not connect to archive.ubuntu.com:80 (91.189.92.172). - connect (111: Connection refused) [IP: 91.189.92.172 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.172 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.172 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.172 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.172 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.172 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.172 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.172 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111: Connection refused) [IP: 91.189.88.37 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2  Unable to connect to security.ubuntu.com:http: [IP: 91.189.88.37 80]
```

I'm puzzled as to what's wrong.  I can ping the IPs mentioned, but if I try to telnet to them on port 80, I instantly get a "connection refused" message.  I can access port 80 on other hosts with no problem, however.

I checked my apt sources.list file and it looks fine.  It's identical to the files for other servers that are working fine.

This machine is *not* behind a proxy, so that's not the issue.  It has an address on the public Internet.

Strangely, I have another virtual machine, also running Ubuntu 10.04 and on the same physical host machine, with the exact same networking configuration.  The only difference between the two machines is that their IP addresses are one number apart.  "apt-get update" works fine on one machine, but not on the other.

Any suggestions?  I'm really puzzled.

---

### Post by pytheas22 on 2010-11-01
I edited /etc/apt/sources.list to change each instance of "http://archive.ubuntu.com/ubuntu" (there were two instances) to "http://de.archive.ubuntu.com/ubuntu" (note the de).  It now works, but I'd love to know why.

Strangely, I also tried switching to [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu), and that didn't work.  The server's in the United States.

---

