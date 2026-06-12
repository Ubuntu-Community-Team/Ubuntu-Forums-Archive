---
title: "ssh access problem"
date: 2014-03-05
forum: Server Platforms
---

### Post by iebo on 2014-03-05
hello friends 


i'm getting this error when i try to access vps

the pw is correct... but not able to authenticate  :(
```
Permission denied (publickey,password).

```

rebooting or re-install the system doesn’t solve this issue 

its low-end server and tech's from hosting  are not willing to support  before sending them unreasonable amount of funds


thnx , hope i get helpful answers from linux gurus

---

### Post by guptesh on 2014-03-06
Check for: "PasswordAuthentication yes" on vps ssh configuration.

OR

you can use public key if you do not want to put in a password everytime.

On your server 

     Code:
     sudo apt-get install ssh 
On your personal computer

     Code:
     ssh-keygen 
Enter through all the prompts... no password.

     Code:
     cd /home/username/.ssh 
     Code:
     vi id_rsa.pub 
Copy all the text in here

type      Code:
     :q! 
 to exit

ssh to your server

     Code:
     cd .ssh 
     Code:
     nano authorized_keys 
paste contents

CTRL+X then Y to save

exit out of the ssh

ssh to your server again... should not ask for password anymore.

---

### Post by iebo on 2014-03-06
hello thank u gup

i did tried this fix before posting my thread 

[http://ubuntuforums.org/showthread.php?t=1860073](http://ubuntuforums.org/showthread.php?t=1860073)


still not working :(

Permission denied (publickey,password).

---

### Post by guptesh on 2014-03-06
post your vps sshd_config configuration and -vvv verbose output of ur attempt.
also try,
ssh -o PreferredAuthentications=keyboard-interactive -o PubkeyAuthentication=no host.example.com
and 
ssh -o PreferredAuthentications=password -o PubkeyAuthentication=no host.example.com

---

### Post by iebo on 2014-03-06
sshd config file on vps:

```
# Package generated configuration file
# See the sshd_config(5) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes

PubkeyAuthentication yes
#AuthorizedKeysFile     %h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
                               
IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server


# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM yes


```


my attempt from pc

```
OpenSSH_5.9p1 Debian-5ubuntu1.1, OpenSSL 1.0.1 14 Mar 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 106.102.88.11 [106.102.88.11] port 22.
debug1: Connection established.
debug3: Incorrect RSA1 identifier
debug3: Could not load "/home/nono/.ssh/id_rsa" as a RSA1 public key
debug1: identity file /home/nono/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/nono/.ssh/id_rsa-cert type -1
debug1: identity file /home/nono/.ssh/id_dsa type -1
debug1: identity file /home/nono/.ssh/id_dsa-cert type -1
debug1: identity file /home/nono/.ssh/id_ecdsa type -1
debug1: identity file /home/nono/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.5p1 Debian-6+squeeze1
debug1: match: OpenSSH_5.5p1 Debian-6+squeeze1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1.1
debug2: fd 3 setting O_NONBLOCK
debug3: load_hostkeys: loading entries for host "106.102.88.11" from file "/home/nono/.ssh/known_hosts"
debug3: load_hostkeys: found key type RSA in file /home/nono/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys
debug3: order_hostkeyalgs: prefer hostkeyalgs: ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-rsa
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-rsa,ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-dss-cert-v00@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-ctr hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 128/256
debug2: bits set: 495/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Server host key: RSA f4:k4:d0:b7:18:12:b5:8f:b3:86:98:92:24:f1:8u:b3
debug3: load_hostkeys: loading entries for host "106.102.88.11" from file "/home/nono/.ssh/known_hosts"
debug3: load_hostkeys: found key type RSA in file /home/nono/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys
debug1: Host '106.102.88.11' is known and matches the RSA host key.
debug1: Found key in /home/nono/.ssh/known_hosts:1
debug2: bits set: 520/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/nono/.ssh/id_rsa (0x21b46ac8)
debug2: key: /home/nono/.ssh/id_dsa ((nil))
debug2: key: /home/nono/.ssh/id_ecdsa ((nil))
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/nono/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/nono/.ssh/id_dsa
debug3: no such identity: /home/nono/.ssh/id_dsa
debug1: Trying private key: /home/nono/.ssh/id_ecdsa
debug3: no such identity: /home/nono/.ssh/id_ecdsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password


```

thanks

---

### Post by guptesh on 2014-03-06
any luck with below commands???

ssh -o PreferredAuthentications=keyboard-interactive -o PubkeyAuthentication=no host.example.com
and 
ssh -o PreferredAuthentications=password -o PubkeyAuthentication=no host.example.com

---

### Post by iebo on 2014-03-06
ok i did check them on terminal .. 

ask for password again then 

Permission denied (publickey,password).

---

### Post by guptesh on 2014-03-06
do you have permission for generated key file?

---

### Post by iebo on 2014-03-06
u mean i have changed permission using chmod ?

---

### Post by guptesh on 2014-03-06
uncomment this line #AuthorizedKeysFile     %h/.ssh/authorized_keys in sshd_config. Now restart service and try again.

---

### Post by iebo on 2014-03-06
ok..

---

### Post by guptesh on 2014-03-06
is it working?

---

### Post by iebo on 2014-03-06
no unfortunately !

---

### Post by guptesh on 2014-03-06
U better try this [https://kb.mediatemple.net/questions/1626/Using+SSH+keys+on+your+server](https://kb.mediatemple.net/questions/1626/Using+SSH+keys+on+your+server)

---

### Post by iebo on 2014-03-06
i gotta sleep now
 will inform u with results  when i get up ;) 

thanks again

---

### Post by iebo on 2014-03-06
hello

i followed the tut though the error-message still exist 

hope more guys help me

---

