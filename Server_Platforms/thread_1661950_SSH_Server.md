---
title: "SSH Server"
date: 2011-01-07
forum: Server Platforms
---

### Post by triunenature on 2011-01-07
I am merely trying to change the port for my ssh server.  However it isn't changing.

I edited my ssh_config file to:

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
    Port 443
#   ForwardAgent no
#   ForwardX11 no
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
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
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
#   VisualHostKey no
#   ProxyCommand ssh -q -W %h:%p gateway.example.com
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no

```

Then restarted ssh via
```
sudo /etc/init.d/ssh restart 
```

When i try to connect to my server via port 443 i get a connection refused error.  However when i try to connect via port 22 it connects.  Since that didn't work, i tried restarting the entire server.

To restate, i changed the config file and restarted ssh then the computer, however the port didn't change.

Ohh and yes my router is set to port forwarding on port 443, though it doesn't matter since I'm inside the network

Thank you

---

### Post by stlsaint on 2011-01-07
You are editing the wrong file. You need to edit the:
sshd_config

```

nano /etc/ssh/sshd_config 
```

---

### Post by triunenature on 2011-01-07
Never mind...

Might help if i edit, sshd_config instead of ssh_config

---

### Post by stlsaint on 2011-01-07
Ignore post

---

### Post by stlsaint on 2011-01-07
Double post. Network issue.

---

