---
title: "Disabling root user via ssh on 18.04"
date: 2019-02-20
forum: Server Platforms
---

### Post by Drone4four on 2019-02-20
Howdy!

I am reconfiguring a DigitalOcean from scratch.  I am enforcing basic security practices. I&#8217;ve got rsa keys configured almost too well.

I&#8217;ve temporarily allowed root login via ssh and now I am trying to turn it off.

Among other guides and questions around the net, I&#8217;ve referenced &#8220;[SSHD_CONFIG - SSH SERVER CONFIGURATION]("https://www.ssh.com/ssh/sshd_config/")&#8221; and "[Permission denied (publickey) when I try to ssh]("https://www.digitalocean.com/community/questions/error-permission-denied-publickey-when-i-try-to-ssh")&#8221;. The guide I originally followed was called &#8220;[Initial Server Setup with Ubuntu 18.04]("https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-18-04")&#8221;.

I&#8217;m missing something here because inside my /etc/ssh/ssh_config I explicitly added:

```
PermitRootLogin no
DenyUsers root
```

After making these changes with sudo I then restarted my ssh daemon with: ```
$ sudo systemctl restart sshd
```

...and yet, root is still able to ssh in. My question for all of you: How do I stop this?

Here are the contents of this file in full:

```

# This is the ssh client system-wide configuration file.  See
# ssh_config(5) for more information.  This file provides defaults for
# users, and the values can be changed in per-user configuration files
# or on the command line.

# Configuration data is parsed as follows:
#  1. command line options
#  2. user-specific file
#  3. system-wide file
# Any configuration value is only changed the first time it is set.
# Thus, host-specific definitions should be at the beginning of the
# configuration file, and defaults at the end.

# Site-wide defaults for some commonly used options.  For a comprehensive
# list of available options, their meanings and defaults, please see the
# ssh_config(5) man page.

Host *
#   ForwardAgent no
#   ForwardX11 no
#   ForwardX11Trusted yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   GSSAPIAuthentication no
#   GSSAPIDelegateCredentials no
#   GSSAPIKeyExchange no
#   GSSAPITrustDNS no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   IdentityFile ~/.ssh/id_ecdsa
#   IdentityFile ~/.ssh/id_ed25519
#   Port 22
#   Protocol 2
#   Ciphers aes128-ctr,aes192-ctr,aes256-ctr,aes128-cbc,3des-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
#   VisualHostKey no
#   ProxyCommand ssh -q -W %h:%p gateway.example.com
#   RekeyLimit 1G 1h
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    PermitRootLogin no
    DenyUsers root

```

Take note of the inclusion of the last 2 lines there. With those lines, I shouldn't be able to login as root, correct?

---

### Post by TheFu on 2019-02-21
/etc/ssh/ssh_config is the client file. Client-side settings don't help on the sshd daemon.
You want /etc/ssh/ssh**d**_config

There are many more things to secure ssh.

BTW, why not use elliptical keys, Ed25519, instead of 20+ yr old RSA and if you want lots-o-security, setup kerberos and 2FA.

---

### Post by Drone4four on 2019-02-23
Thanks **@TheFu**!

These two configuration files have very similar names. That clarifies. 

I'll look into Ed25519.

---

### Post by TheFu on 2019-02-24
If this is solved, do the community a favor and use the "thread tools" button near the top.

[http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) has more about securing ssh, like how to allow selective IPs to ssh in as root, but only using keys.  That is good for performing "pull" backups, a best practice.

---

