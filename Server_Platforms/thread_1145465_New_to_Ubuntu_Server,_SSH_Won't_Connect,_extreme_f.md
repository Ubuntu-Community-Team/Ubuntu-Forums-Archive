---
title: "New to Ubuntu Server, SSH Won't Connect, extreme frustration"
date: 2009-05-01
forum: Server Platforms
---

### Post by Willberto on 2009-05-01
I'm setting up a web server using Ubuntu Server to have a test area for PHP/MySQL.  I set it up using the desktop version several times and it worked fine.  But now when I try to SSH into it, a process that has always worked flawlessly, has now drove me to extreme frustration.  This is day 2 of trying to get it to work.

Guides have been no help so far.

Edit:  ssh localhost works fine on both machines.

```
will@will-desktop:~$ ssh -v will@192.168.0.101
OpenSSH_5.1p1 Debian-3ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config   
debug1: Applying options for *                           
debug1: Connecting to 192.168.0.101 [192.168.0.101] port 22.
debug1: Connection established.                             
debug1: identity file /home/will/.ssh/identity type -1      
debug1: identity file /home/will/.ssh/id_rsa type -1        
debug1: identity file /home/will/.ssh/id_dsa type -1        
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-5ubuntu1
debug1: match: OpenSSH_5.1p1 Debian-5ubuntu1 pat OpenSSH*                                 
debug1: Enabling compatibility mode for protocol 2.0                                      
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-3ubuntu1                        
debug1: SSH2_MSG_KEXINIT sent                                                             
debug1: SSH2_MSG_KEXINIT received                                                         
debug1: kex: server->client aes128-cbc hmac-md5 none                                      
debug1: kex: client->server aes128-cbc hmac-md5 none                                      
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent                                  
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP                                               
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent                                                     
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '192.168.0.101' is known and matches the RSA host key.
debug1: Found key in /home/will/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/will/.ssh/identity
debug1: Trying private key: /home/will/.ssh/id_rsa
debug1: Trying private key: /home/will/.ssh/id_dsa
debug1: Next authentication method: password
will@192.168.0.101's password:
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.
will@192.168.0.101's password:
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.
will@192.168.0.101's password:
debug1: Authentications that can continue: publickey,password
debug1: No more authentication methods to try.
Permission denied (publickey,password).
will@will-desktop:~$

```

---

### Post by brian_p on 2009-05-01
> **Willberto said:**
> I'm setting up a web server using Ubuntu Server to have a test area for PHP/MySQL.  I set it up using the desktop version several times and it worked fine.  But now when I try to SSH into it, a process that has always worked flawlessly, has now drove me to extreme frustration.  This is day 2 of trying to get it to work.

A quick comparison with what I get from ssh -v shows responses identical (as far I can see) to what you get. It looks like 192.168.0.101 does not like the password you give. But if the same password gets you in with ssh localhost . . . . !

You could try changing the password on 192.168.0.101.

---

### Post by Willberto on 2009-05-01
Problem solved!

It looks like it didn't like the format of my password.  I'm not going to dive too much into it, but I'm guessing it didn't like an apostrophe.

Thanks for the suggestion, you solved it!

---

### Post by HermanAB on 2009-05-01
Hmm, in Bash, it is not an Apostrophe, it is a Single Quote and Single and Double Quotes have special meanings and must always be paired.

---

### Post by Willberto on 2009-05-01
I suspected something to do with that.  Thanks for the info.

What I get for trying to make up secure passwords.  :)

---

### Post by brian_p on 2009-05-02
> **Willberto said:**
> 

What I get for trying to make up secure passwords.  :)

You can get that with length and a moderate amount of complexity. And have it memorable too.

e.g !!MydoghasnonoseHowdoesitsmell??

---

