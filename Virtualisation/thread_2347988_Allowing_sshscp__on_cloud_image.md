---
title: "Allowing ssh/scp  on cloud image"
date: 2016-12-30
forum: Virtualisation
---

### Post by pages on 2016-12-30
Hey all ,

I'm new to the "world of virtualisation" and messing about with openstack. 
For the company i'm in we're looking at setting up an on premise private cloud for our github and also all the developer machines so that the source code technically never leaves the location.


So I know when creating the VMs there's an option to import ssh keys so that it's password-less authentication. But I find this kinda limiting ?
I know the logic is it makes it more secure but it seems to make it actually harder to work!  

Like for example we use third party vendors for development work so they can be changed depending on our demand. When we spawn a new VM for them, it'll be set up so they can remote into the desktop and develop away but it seems rather limiting that they can't ssh in to the machine itself. For example last night I wanted to import the company .cer file on the machine to get past the firewall but I couldnt scp the file either as there user in the VNC session  :/ It just seemed like to me that it'll create additional headaches that could be avoided

So rather long winded post but was looking at ```
/etc/ssh/sshd_config 
```and I'm not exactly sure what it's missing to allow remote login. There was one setting```
 UseLogin 
``` which I set to yes. But still no joy with trying to access the machine. 
Is there something simple I'm missing to allow this ?

---

### Post by SeijiSensei on 2016-12-30
I don't know about Openstack, but in VirtualBox you need to state explicitly that you want the network connection to be "bridged."  That means it gets an IP address on the same network as the VM host machine.  Otherwise the VM uses NAT and is invisible from outside the host machine.  

Just to make sure it's not a problem like this, can you ping the VM from other machines on the network?

---

### Post by pages on 2016-12-30
Hey,  

Yeah the machine is assigned a floating IP address so it's completely reachable from our network.  Just the issue seems to be that ssh without a ssh key is not allowed.  Like as I say it's not the end of the world for a developer who's vnc'd in but I just know I'd like the ability to have Winscp access to any machine I'm remoting into

---

### Post by SeijiSensei on 2016-12-31
Connect from another machine using Linux, and run the SSH client in verbose mode like this:
```
ssh -v server_name
```
If one "v" doesn't provide enough detail (though it should), use two.  Also what do you see in /var/log/auth.log when you connect to the SSH server?

Sometimes the system will hang for quite a while during authentication if you have 
```
GSSAuthentication yes
```
in /etc/ssh/sshd_config.  Set that to no.  That problem will be immediately visible if you use -v from a remote client.

---

### Post by pages on 2017-01-01
Sorry for the delayed response only back to the computer now.
```
$ ssh -v test@172.16.2.139OpenSSH_6.6.1, OpenSSL 1.0.1e-fips 11 Feb 2013
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 56: Applying options for *
debug1: Connecting to 172.16.2.139 [172.16.2.139] port 22.
debug1: Connection established.
debug1: identity file /home/admin/.ssh/id_rsa type 1
debug1: identity file /home/admin/.ssh/id_rsa-cert type -1
debug1: identity file /home/admin/.ssh/id_dsa type -1
debug1: identity file /home/admin/.ssh/id_dsa-cert type -1
debug1: identity file /home/admin/.ssh/id_ecdsa type -1
debug1: identity file /home/admin/.ssh/id_ecdsa-cert type -1
debug1: identity file /home/admin/.ssh/id_ed25519 type -1
debug1: identity file /home/admin/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.6.1
debug1: Remote protocol version 2.0, remote software version OpenSSH_7.2p2 Ubuntu-4ubuntu2.1
debug1: match: OpenSSH_7.2p2 Ubuntu-4ubuntu2.1 pat OpenSSH* compat 0x04000000
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-sha1-etm@openssh.com none
debug1: kex: client->server aes128-ctr hmac-sha1-etm@openssh.com none
debug1: kex: curve25519-sha256@libssh.org need=20 dh_need=20
debug1: kex: curve25519-sha256@libssh.org need=20 dh_need=20
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA 7d:67:53:5c:eb:31:91:6a:97:18:c6:24:80:19:63:f0
debug1: Host '172.16.2.139' is known and matches the ECDSA host key.
debug1: Found key in /home/admin/.ssh/known_hosts:3
debug1: ssh_ecdsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/admin/.ssh/id_rsa
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/admin/.ssh/id_dsa
debug1: Trying private key: /home/admin/.ssh/id_ecdsa
debug1: Trying private key: /home/admin/.ssh/id_ed25519
debug1: No more authentication methods to try.
Permission denied (publickey).



```

Seems the cloud image of ubuntu is stopping after publickey instead of trying password. 
Here's the ssh_config 


```
Host *#   ForwardAgent no
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
#   IdentityFile ~/.ssh/id_ecdsa
#   IdentityFile ~/.ssh/id_ed25519
#   Port 22
#   Protocol 2
#   Cipher 3des
#   Ciphers aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
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
    GSSAPIDelegateCredentials no



```

---

