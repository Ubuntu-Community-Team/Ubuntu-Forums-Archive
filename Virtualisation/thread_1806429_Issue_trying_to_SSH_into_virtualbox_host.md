---
title: "Issue trying to SSH into virtualbox host"
date: 2011-07-17
forum: Virtualisation
---

### Post by alzaf on 2011-07-17
I've got Ubuntu 11.04 installed as host and virtualbox OSE 4.04 guest which I am using to test a LAMP server. I have got a successful Apache test page when using the following link 

[http://localhost:8888/](http://localhost:8888/)

I also got a successful PHP test with the following link:

[http://localhost:8888/info.php](http://localhost:8888/info.php)

and testing MySQl server using phpMyAdmin 

[http://localhost:8888/phpmyadmin/](http://localhost:8888/phpmyadmin/) 

However when I try to ssh into Virtual box guest, I get the following error:

```
Permission denied, please try again.
```

I'm still a noob to networking so apologies in advances for information that is not relevant. I've been working on this for a couple of days and getting no where hence reason why I'm posting. After googling I have done various things but the one I remember doing are as follows:

* Installed openssh in both host and guest
* Added following information to Virtualbox:

```

Key: VBoxInternal/Devices/pcnet/0/LUN#0/Config/Apache/GuestPort, Value: 80
Key: VBoxInternal/Devices/pcnet/0/LUN#0/Config/Apache/HostPort, Value: 8888
Key: VBoxInternal/Devices/pcnet/0/LUN#0/Config/Apache/Protocol, Value: TCP
Key: VBoxInternal/Devices/pcnet/0/LUN#0/Config/ssh/GuestPort, Value: 22
Key: VBoxInternal/Devices/pcnet/0/LUN#0/Config/ssh/HostPort, Value: 2222
Key: VBoxInternal/Devices/pcnet/0/LUN#0/Config/ssh/Protocol, Value: TCP

```

*Made amendment to /etc/ssh/sshd_config:
  Port 2222

* Opened up ports via iptables in both host and guest
* Added "allowUsers <name>" to  /etc/ssh/sshd_config in guest.


For info, this is the last 10 entries of /var/auth.log on host:

```
Jul 17 22:31:28 user sshd[2978]: pam_unix(sshd:auth): check pass; user unknown
Jul 17 22:31:28 user sshd[2978]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=localhost 
Jul 17 22:31:30 user sshd[2978]: Failed password for invalid user tst from 127.0.0.1 port 35311 ssh2
Jul 17 22:32:58 user sudo:   user : TTY=pts/1 ; PWD=/home/user ; USER=root ; COMMAND=/usr/bin/ssh -l tst -p 2222 localhost
Jul 17 22:32:58 user sshd[2983]: Invalid user tst from 127.0.0.1
Jul 17 22:33:08 user sudo:   user : TTY=pts/1 ; PWD=/home/user ; USER=root ; COMMAND=/usr/bin/ssh -l test -p 2222 localhost
Jul 17 22:33:08 user sshd[2987]: Invalid user test from 127.0.0.1
Jul 17 22:33:10 user sshd[2987]: pam_unix(sshd:auth): check pass; user unknown
Jul 17 22:33:10 user sshd[2987]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=localhost 
Jul 17 22:33:12 user sshd[2987]: Failed password for invalid user test from 127.0.0.1 port 33229 ssh2

```

EDIT:
I'm sure i've opened up the ports correctly with following with following commands:

```
sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
sudo iptables -A OUTPUT -p tcp --sport 22 -j ACCEPT

```

but the following command

ssh -vv test@localhost

produces the following results:

```
OpenSSH_5.8p1 Debian-1ubuntu3, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to localhost [127.0.0.1] port 22.
debug1: connect to address 127.0.0.1 port 22: Connection refused
ssh: connect to host localhost port 22: Connection refused
```

I also ran the following command:

netstat -ln | grep 22

and got output

```
tcp        0      0 0.0.0.0:2222            0.0.0.0:*               LISTEN     
tcp        0      0 81.106.244.224:53       0.0.0.0:*               LISTEN     
tcp6       0      0 :::2222                 :::*                    LISTEN     
udp        0      0 81.106.244.224:53       0.0.0.0:*                          
unix  2      [ ACC ]     STREAM     LISTENING     12415    /tmp/orbit-user/linc-5a1-0-22e7b576f0b63

```

Thanks in advance for help given.

---

### Post by gmargo on 2011-07-17
Look at your **netstat** output.  You are only listening on port 2222.  Not port 22.

---

### Post by CharlesA on 2011-07-18
Are you trying to get from the guest to the host? If so, use the ip address of the host.

---

### Post by alzaf on 2011-07-18
gmargo, I'm getting mixed up with Guest and Host config. Virtualbox has being configured to monitor port 2222 on host and port 22 on guest. I've opened port 2222 on Host and got the following output using sudo ssh -vvv test@localhost

```
OpenSSH_5.8p1 Debian-1ubuntu3, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to localhost [127.0.0.1] port 2222.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/id_rsa type -1
debug1: identity file /root/.ssh/id_rsa-cert type -1
debug3: Incorrect RSA1 identifier
debug3: Could not load "/root/.ssh/id_dsa" as a RSA1 public key
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /root/.ssh/id_dsa type 2
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: identity file /root/.ssh/id_dsa-cert type -1
debug1: identity file /root/.ssh/id_ecdsa type -1
debug1: identity file /root/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.8p1 Debian-1ubuntu3
debug1: match: OpenSSH_5.8p1 Debian-1ubuntu3 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.8p1 Debian-1ubuntu3
debug2: fd 3 setting O_NONBLOCK
debug3: put_host_port: [localhost]:2222
debug3: load_hostkeys: loading entries for host "[localhost]:2222" from file "/root/.ssh/known_hosts"
debug3: load_hostkeys: found key type RSA in file /root/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys
debug3: order_hostkeyalgs: prefer hostkeyalgs: ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-rsa
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-rsa,ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-dss-cert-v00@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss,ecdsa-sha2-nistp256
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
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: RSA 0a:fc:6c:4b:16:d1:30:e3:d0:04:7c:66:50:fb:de:5d
debug3: put_host_port: [127.0.0.1]:2222
debug3: put_host_port: [localhost]:2222
debug3: load_hostkeys: loading entries for host "[localhost]:2222" from file "/root/.ssh/known_hosts"
debug3: load_hostkeys: found key type RSA in file /root/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys
debug1: Host '[localhost]:2222' is known and matches the RSA host key.
debug1: Found key in /root/.ssh/known_hosts:1
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
debug2: key: /root/.ssh/id_rsa ((nil))
debug2: key: /root/.ssh/id_dsa (0x21f7c090)
debug2: key: /root/.ssh/id_ecdsa ((nil))
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /root/.ssh/id_rsa
debug3: no such identity: /root/.ssh/id_rsa
debug1: Offering DSA public key: /root/.ssh/id_dsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /root/.ssh/id_ecdsa
debug3: no such identity: /root/.ssh/id_ecdsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
test@localhost's password: 
debug3: packet_send2: adding 64 (len 55 padlen 9 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.

```

It looks like it could be to do with public keys. I had googled about this and it was mentioned I needed to copy public keys from host to guest. I'll try that in the next few days.

CharlesA, I'm trying to access guest from console on host.

---

### Post by CharlesA on 2011-07-19
Can you just use a password instead of keys while you are troubleshooting?

---

### Post by alzaf on 2011-07-25
> **CharlesA said:**
> Can you just use a password instead of keys while you are troubleshooting?

Have been caught up with other things so only now been able to get back to this.

I'm using password only as per debug message when using ssh -vvv

```
debug1: Authentications that can continue: password
```

but I am getting same Permission denied error message. I noticed the output from /var/log/auth.log


```
Jul 25 18:23:03 user sudo:   user : TTY=pts/1 ; PWD=/etc/ssh ; USER=root ; COMMAND=/usr/bin/ssh -vvv test.test@localhost
Jul 25 18:23:03 user sshd[2240]: Invalid user test.test from 127.0.0.1
Jul 25 18:23:05 user sshd[2240]: pam_unix(sshd:auth): check pass; user unknown
Jul 25 18:23:05 user sshd[2240]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=localhost 
Jul 25 18:23:07 user sshd[2240]: Failed password for invalid user test.test from 127.0.0.1 port 60174 ssh2
```

I'm not sure if the issue could be with the way I am trying to log into account temp on guest. The user name and password is correct but I tried with on it's own and with hostname which is test as well (I have tinkering with ssh'ing into virtalbox a year or two ago and I'm sure I had used the hostname). The unsuccessful logins were done with the following commands:

```

sudo ssh -vvv test.temp@localhost
sudo ssh -vvv test@localhost

```

Could this be what the issue is?

---

### Post by alzaf on 2011-07-25
Could it be that virtualbox is not listening to port 2222?

The following command:

```
sudo netstat --tcp --udp --listening --program
```

gives output:

```
 tcp        0      0 *:2222                  *:*                     LISTEN      1831/sshd       
tcp        0      0 cpc2-grnk3-0-0-c:domain *:*                     LISTEN      1068/named      
tcp        0      0 localhost:domain        *:*                     LISTEN      1068/named      
tcp        0      0 localhost:ipp           *:*                     LISTEN      897/cupsd       
tcp        0      0 *:8888                  *:*                     LISTEN      1708/VirtualBox 
tcp        0      0 *:6969                  *:*                     LISTEN      1109/aped       
tcp        0      0 localhost:953           *:*                     LISTEN      1068/named      
tcp6       0      0 [::]:2222               [::]:*                  LISTEN      1831/sshd       
tcp6       0      0 [::]:domain             [::]:*                  LISTEN      1068/named      
tcp6       0      0 ip6-localhost:ipp       [::]:*                  LISTEN      897/cupsd       
tcp6       0      0 ip6-localhost:953       [::]:*                  LISTEN      1068/named      
udp        0      0 cpc2-grnk3-0-0-c:domain *:*                                 1068/named      
udp        0      0 localhost:domain        *:*                                 1068/named      
udp        0      0 *:bootpc                *:*                                 1197/dhclient   
udp        0      0 *:46200                 *:*                                 1708/VirtualBox 
udp        0      0 *:mdns                  *:*                                 908/avahi-daemon: r
udp        0      0 *:51463                 *:*                                 908/avahi-daemon: r
udp        0      0 *:43822                 *:*                                 1708/VirtualBox 
udp        0      0 *:36162                 *:*                                 1708/VirtualBox 
udp6       0      0 [::]:domain             [::]:*                              1068/named      
udp6       0      0 [::]:mdns               [::]:*                              908/avahi-daemon: r
udp6       0      0 [::]:60828              [::]:*                              908/avahi-daemon: r
```

but virtualbox is setup to listen to port 2222 on host as per settings:

```
Key: GUI/LastCloseAction, Value: save
Key: GUI/LastGuestSizeHint, Value: 1024,768
Key: GUI/LastNormalWindowPosition, Value: 1,22,1024,708
Key: GUI/MiniToolBarAlignment, Value: bottom
Key: GUI/SaveMountedAtRuntime, Value: yes
Key: GUI/ShowMiniToolBar, Value: yes
Key: VBoxInternal/Devices/pcnet/0/LUN#0/Config/Apache/GuestPort, Value: 80
Key: VBoxInternal/Devices/pcnet/0/LUN#0/Config/Apache/HostPort, Value: 8888
Key: VBoxInternal/Devices/pcnet/0/LUN#0/Config/Apache/Protocol, Value: TCP
Key: VBoxInternal/Devices/pcnet/0/LUN#0/Config/ssh/GuestPort, Value: 22
Key: VBoxInternal/Devices/pcnet/0/LUN#0/Config/ssh/HostPort, Value: 2222
Key: VBoxInternal/Devices/pcnet/0/LUN#0/Config/ssh/Protocol, Value: TCP
```

EDIT: I amended /etc/ssh/sshd_config so that port 22 is being listened to and when running above netstat command, it shows that Virtualbox is listening to port 222 as per output

```
tcp        0      0 *:2222                  *:*                     LISTEN      1954/VirtualBox 
```
 
Unfortunately I still getting same error.

---

### Post by CharlesA on 2011-07-26
Is there a reason why you are using the internal adapter instead of just using bridged networking?

---

### Post by alzaf on 2011-07-26
> **CharlesA said:**
> Is there a reason why you are using the internal adapter instead of just using bridged networking?

I am a newbie to networking but I had been playing around with Virtualbox a year or two ago and had no problems SSH'ing into the guest with port forwarding with NAT then. I have done all the things that I can remember doing them but I'm still stuck. 

Just also to keep in mind that with internal adapter I can access the Apache server in guest so I should be able to SSH in.

---

### Post by CharlesA on 2011-07-26
Hmm yeah, if you can access apache, you should be able to access ssh.

It looks like you can connect but it fails due to using an invalid username.

---

