---
title: "How to remove  umac-64@openssh.com MAC in OpenSSH 7.6"
date: 2020-05-21
forum: Security
---

### Post by ndilgard on 2020-05-21
Our recent vulnerability scan results showed that OpenSSH 7.6 on our  Ubuntu 18.04.4 LTS server is using the [email]umac-64@openssh.com[/email] MAC. I  searched for the MAC line in the ssh_config file and noticed the line was commented out. I remove the # and remove [email]umac-64@openssh.com[/email] from the line and restarted the service. The only remaining MACs in the configuration file are hmac-md5, hmac-sha1. However, when I run a scan the finding still shows up. I checked the MACs with Nmap using the ssh2-enum-algos script and not only is the [email]umac-64@openssh.com[/email] MAC still there, but there are also a lot more MACs that are not mentioned in the ssh_config file. The output of the Nmap results is posted below. Did I miss something? Is there another configuration file that needs to be changed?

```
PORT     STATE  SERVICE
22/tcp   open   ssh
| ssh2-enum-algos:
|   kex_algorithms: (10)
|       curve25519-sha256
|       curve25519-sha256@libssh.org
|       ecdh-sha2-nistp256
|       ecdh-sha2-nistp384
|       ecdh-sha2-nistp521
|       diffie-hellman-group-exchange-sha256
|       diffie-hellman-group16-sha512
|       diffie-hellman-group18-sha512
|       diffie-hellman-group14-sha256
|       diffie-hellman-group14-sha1
|   server_host_key_algorithms: (5)
|       ssh-rsa
|       rsa-sha2-512
|       rsa-sha2-256
|       ecdsa-sha2-nistp256
|       ssh-ed25519
|   encryption_algorithms: (6)
|       chacha20-poly1305@openssh.com
|       aes128-ctr
|       aes192-ctr
|       aes256-ctr
|       aes128-gcm@openssh.com
|       aes256-gcm@openssh.com
|   mac_algorithms: (10)
|       umac-64-etm@openssh.com
|       umac-128-etm@openssh.com
|       hmac-sha2-256-etm@openssh.com
|       hmac-sha2-512-etm@openssh.com
|       hmac-sha1-etm@openssh.com
|       umac-64@openssh.com
|       umac-128@openssh.com
|       hmac-sha2-256
|       hmac-sha2-512
|       hmac-sha1
|   compression_algorithms: (2)
|       none
|_     zlib@openssh.com
```

---

### Post by EuclideanCoffee on 2020-05-21
I cannot say unless I have more context.

It appears you may not have correctly configured the file and restarted the service.

Your MACs and Ciphers should be formatted like this:

```

Ciphers chacha20-poly1305@openssh.com,aes256-gcm@openssh.com,aes128-gcm@openssh.com,aes256-ctr,aes192-ctr,aes128-ctr
KexAlgorithms curve25519-sha256@libssh.org,diffie-hellman-group-exchange-sha256
MACs hmac-sha2-512-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-ripemd160-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-512,hmac-sha2-256,hmac-ripemd160,umac-128@openssh.com


```

Please note that each line beings with a keyword.

---

### Post by DuckHook on 2020-05-21
Welcome to the Forums, ndilgard.

Please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by philhughes on 2020-05-22
First of all, the nmap scan is showing you the server configuration, but you have edited ssh_config, which is the client configuration file. You need to edit sshd_config.

Second, in general, commented-out entries in the ssh config files show default values, as noted at the top of sshd_config. So by removing the entry, you will not change anything. To remove a specific mac, you will need an entry in sshd_config like this:

```
MACs -umac-64@openssh.com
```

Note the preceeding '-' sign.

You can print out the entire sshd configuration with:

```
sudo sshd -T
```

See man sshd_config for more information.

---

