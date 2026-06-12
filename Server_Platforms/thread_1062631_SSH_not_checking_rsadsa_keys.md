---
title: "SSH not checking rsa/dsa keys"
date: 2009-02-07
forum: Server Platforms
---

### Post by Causer1984 on 2009-02-07
I cannot get my box to get passwordless RSA/DSA ssh authentication. I'm pretty sure it's a config issue, but I can't see what's going wrong. I've done the necessary ssh-keygen on the computer I want to ssh from and copied id_rsa.pub to the server and concated it to authorized_keys2. I cannot RSA log in using localhost (it asks for a password) and I've used the public RSA key to ssh into other computers.

The computer came as a package VM, so I don't know what state it arrived in.

```

cat /etc/ssh/ssh_config                                                                   

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
#   StrictHostKeyChecking no
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   Port 22
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no



```

```

SSHING INTO COMPUTER
$ ssh user@computer-in-question.com

[snip]
debug2: key: /home/user/.ssh/id_rsa (0xb9df5a80)
debug2: key: /home/user/.ssh/identity ((nil))
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering public key: /home/user/.ssh/id_dsa
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Offering public key: /home/user/.ssh/id_rsa
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/user/.ssh/identity
debug2: we did not send a packet, disable method
debug1: Next authentication method: password
user@computer-in-question password:

```

Any help appreciated.

---

### Post by petersenmde on 2009-02-07
What does your /etc/ssh/sshd_config file look like?

It should have:

usePAM no
PasswordAuthentication no
ChallengeResponseAuthentication no
RSAAuthentication yes
PubkeyAuthentication yes

I recommend setting PermitRootLogin to no, and limiting who can login via ssh with a list of AllowUsers *username*

Mark

---

