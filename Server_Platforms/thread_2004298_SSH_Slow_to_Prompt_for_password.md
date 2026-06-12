---
title: "SSH Slow to Prompt for password"
date: 2012-06-15
forum: Server Platforms
---

### Post by securitymeddler on 2012-06-15
All, 

When SSHing from terminal/bash into out RHEL boxes it takes about 30 seconds for the password prompt to come back to me. Very weird. I don't seem to have this issue with putty. 

Ubuntu 12.04 

Any idea what I might have missed?

---

### Post by SeijiSensei on 2012-06-15
If you're using host names (e.g., "ssh host.example.com") then you must have proper forward and reverse DNS resolution at both ends.  There are ways to avoid this:

1)  Add "UseDNS no" to /etc/ssh/sshd_config on the server and /etc/ssh/ssh_config on the client; or

2)  Set up a DNS server with proper forward and reverse ("in-addr.arpa") records for both the client and server; or

3)  Create entries in the [hosts]("http://en.wikipedia.org/wiki/Hosts_%28file%29") file on both the client and server with the appropriate names and addresses; or

4)  Use IP addresses rather than names.

---

### Post by hawkmage on 2012-06-15
Most of the time when you have a long delay in connecting via ssh to a system it is DNS related.  This is talked about in the OpenSSH FAQ item 3.3: [http://www.openssh.org/faq.html#3.3](http://www.openssh.org/faq.html#3.3)

By default sshd will do a reverse look-up on the incoming IP of a connection and this can cause delays if your systems IP address (IPv4 or IPv6) is not DNS resolvable.  

The usual work around is to add "UseDNS no" to the sshd_config.

---

### Post by kanikilu on 2012-06-15
Beyond the reverse dns lookup issue mentioned, another setting that some people find helps is "GSSAPIAuthentication no" in /etc/ssh/ssh_config on the client.

There are some other suggested workarounds here:

[https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/84899](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/84899)

---

