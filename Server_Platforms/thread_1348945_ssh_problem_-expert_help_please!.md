---
title: "ssh problem -expert help please!"
date: 2009-12-07
forum: Server Platforms
---

### Post by Muttley99 on 2009-12-07
I have carefully followed the instructions for setting up a passwordless login using rsa key exchange.
I cannot connect! I get a message 'server refused our key'.
BUT If I connect a keyboard & mouse to the server and login direct; The external computer can connect without password via ssh as long as I am logged in direct!!

I have set permissions on both server & client .ssh/ directory to 700 with all files within this directory to 644.
using 'ssh -v 192.168.0.5' from my client, shows a clean login via ssh as long as I'm logged in at the server.
I have only one user account added on the server 'david'. The client is Kubuntu 9.10.

Please help as I'm losing the will to live after spending hours checking and re-checking.
Thanks in advance!

---

### Post by windependence on 2009-12-07
If you're trying to log in as root it won't work unless you allow root logins (not recommended). You should create a user or use one on the server for the keyless login.

-Tim

---

### Post by Muttley99 on 2009-12-08
I had turned off root login in sshd_config. I'm logging in as a user only.
So why does it block ssh connection normally, but allow ssh connection after I log-in directly to the server?](*,)

---

### Post by Xianath on 2009-12-08
Please post the output of ```
ssh -vvv 192.168.0.5
``` with it not working. This level of debug should tell us something.

Cheers,
Peter

---

### Post by Muttley99 on 2009-12-09
ok here is debug from same client with same command BUT i'm already logged in direct on the server; (basic debug)

[HTML]david@david-desktop:~$ ssh -v @192.168
OpenSSH_5.1p1 Debian-6ubuntu2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to  port 22.
debug1: Connection established.
debug1: identity file /home/david/.ssh/identity type -1
debug1: identity file /home/david/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/david/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-6ubuntu2
debug1: match: OpenSSH_5.1p1 Debian-6ubuntu2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-6ubuntu2
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '192.' is known and matches the RSA host key.
debug1: Found key in /home/david/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/david/.ssh/identity
debug1: Offering public key: /home/david/.ssh/id_rsa
debug1: Server accepts key: pkalg ssh-rsa blen 277
debug1: PEM_read_PrivateKey failed
debug1: read PEM private key done: type <unknown>
Enter passphrase for key '/home/david/.ssh/id_rsa':
debug1: read PEM private key done: type RSA
debug1: Authentication succeeded (publickey).
debug1: channel 0: new [client-session]
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_GB.UTF-8[/HTML]

Ok, I can connect as above as long as I'm already logged in at the server. User on client is same 'id' as on server. This is where is all goes wrong!

Here id the vvv debug you requested!

[HTML]david@david-desktop:~$ ssh -vvv david@192.                               
OpenSSH_5.1p1 Debian-6ubuntu2, OpenSSL 0.9.8g 19 Oct 2007                               
debug1: Reading configuration data /etc/ssh/ssh_config                                  
debug1: Applying options for *                                                          
debug2: ssh_connect: needpriv 0                                                         
debug1: Connecting to 192] port 22.                                
debug1: Connection established.                                                         
debug1: identity file /home/david/.ssh/identity type -1                                 
debug3: Not a RSA1 key file /home/david/.ssh/id_rsa.                                    
debug2: key_type_from_name: unknown key type '-----BEGIN'                               
debug3: key_read: missing keytype                                                       
debug2: key_type_from_name: unknown key type 'Proc-Type:'                               
debug3: key_read: missing keytype                                                       
debug2: key_type_from_name: unknown key type 'DEK-Info:'                                
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
debug3: key_read: missing whitespace                                                    
debug3: key_read: missing whitespace                                                    
debug3: key_read: missing whitespace                                                    
debug3: key_read: missing whitespace                                                    
debug3: key_read: missing whitespace                                                    
debug2: key_type_from_name: unknown key type '-----END'                                 
debug3: key_read: missing keytype                                                       
debug1: identity file /home/david/.ssh/id_rsa type 1                                    
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048                       
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048                             
debug1: identity file /home/david/.ssh/id_dsa type -1                                   
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-6ubuntu2                                                                                      
debug1: match: OpenSSH_5.1p1 Debian-6ubuntu2 pat OpenSSH*                               
debug1: Enabling compatibility mode for protocol 2.0                                    
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-6ubuntu2                      
debug2: fd 3 setting O_NONBLOCK                                                         
debug1: SSH2_MSG_KEXINIT sent                                                           
debug1: SSH2_MSG_KEXINIT received                                                       
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1                       
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss                                              
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr                                                                                
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr                                                                                
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96                                            
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96                                            
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib                                   
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib                                   
debug2: kex_parse_kexinit:                                                              
debug2: kex_parse_kexinit:                                                              
debug2: kex_parse_kexinit: first_kex_follows 0                                          
debug2: kex_parse_kexinit: reserved 0                                                   
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1                       
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss                                              
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr                                                                                
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 123/256
debug2: bits set: 526/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: filename /home/david/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 1
debug1: Host '192.168.0.5' is known and matches the RSA host key.
debug1: Found key in /home/david/.ssh/known_hosts:1
debug2: bits set: 500/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/david/.ssh/identity ((nil))
debug2: key: /home/david/.ssh/id_rsa (0x7ff11b40aa90)
debug2: key: /home/david/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/david/.ssh/identity
debug3: no such identity: /home/david/.ssh/identity
debug1: Offering public key: /home/david/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/david/.ssh/id_dsa
debug3: no such identity: /home/david/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
david@192.'s password:[/HTML]

Above is when I'm not logged in direct to the server!

I have spent hours trying to crack this;
I've both manually pasted the pub key over, cat from within the .ssh directory and ssh-copy-id from the client with the same results.
Also, I've checked the permissions for the .ssh directory and the files within are correct.
the key pair was made by ssh-keygen and I've checked it is a single line in authorized_keys.
I've also set /etc/hosts.allow to accept all: sshd
I'm just going to try making the keys on the server and copying over the private key (though this is not normally a good idea)

any other ideas are very welcome!! :)

---

### Post by Muttley99 on 2009-12-09
....In addition; I've just tried making the keys on the server and passing over the private key to the client - same error!
Also, tried making a 1024 bit key pair instead of the 2048 default and no joy!

/var/log/auth shows this error just as I try and login 

*Error attempting to add filename encryption key to user session keyring; rc = [1]*

Which reminds me I have an encrypted /home directory. I think this maybe the problem!

---

### Post by Muttley99 on 2009-12-09
Confirmed¬#-o

It's obvious now I think about it but i've spent hours messing with this all because i encrypted my home folder.
launchpad bug #362427 has a workaround.

after doing the above keys authenticate and access is granted :D

---

