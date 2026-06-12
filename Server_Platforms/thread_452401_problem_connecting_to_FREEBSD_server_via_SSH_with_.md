---
title: "problem connecting to FREEBSD server via SSH with ubuntu"
date: 2007-05-23
forum: Server Platforms
---

### Post by K-a-M-u-Z-u on 2007-05-23
hi.
i have a FREEBSD host server in a remote location.
i'm trying to connect to it with the following command in terminal:
```
ssh username@ip.address
```
i recieve back "password" and i cant write it.
i mean...its look like it get no input and the marker stay in the same spot.i tried COPY PASTE and again nothing.it says that the password is wrong.
after that i tries i windows with thae program "SSH Secure Shell Client-3.2.5" and everithing is working fine.
so i try to run the same program trough WINE in uuntu.but again.it asks for password but it look like its not getting any input al all...

when i try to make a connection to browse in ubuntu(PLACES->CONNECT TO A SERVER) and i choose SSH and put the user name, nothing happens...i got a new location in the MOUNT point(the IP ADDRESS) with a LOCK on it...

what could be the problem with ubuntu?

---

### Post by atoponce on 2007-05-23
When entering passwords in terminals in Unix-like operating systems, you well never see the echo of the password.  The field will stay blank as you enter in the password.  This is standard behavior since Unix was first introduced in the '70s.

As far as not being able to login, it's probably because either you are typing the password wrong, by copying and pasting it too many times, or just mistyping, or it's not working, because it requires authentication via SSH keys and not passwords.  Now that you know that the password is not echoed to the terminal, try typing in the password again, paying attention to correct spelling, and see if it doesn't work.

This certainly isn't a problem with Ubuntu. :)

---

### Post by K-a-M-u-Z-u on 2007-05-25
thnx.
but still, dosent matter what i do i get:
> Permission denied, please try again.
the language is set to english(USA), there is no CAPS LOCK.i dont COPY-PASTE it. the password is OK. i used it under windows with no problems.i type it exacly as i do under WINDOWS.
only under linux i get that error... :( 
i hate going into windows doing things that linux supose to do best... :\

---

### Post by VorDesigns on 2007-05-26
I have a similar problem; I have been conneting all day long to my new feisty install via putty on several Windows systems.  Just tried to connect using this Dapper install and doesn't matter how I fashion the connection, it gives me a permission denied.

ssh -l user ip_address
ssh user@server ip_addres
ssh [email]user@server.domain.tld[/email] ip_address
ssh -l user [email]user@server.domain.tld[/email] ip_address

---

### Post by mitch.c on 2007-05-26
Maybe if you post the output from an ssh login attempt with the 'verbose' option we could help figure this out:
```
$ ssh -vv user@hostname
```
Is the ssh server configured to use password logins, public key authentication, or both?

---

### Post by VorDesigns on 2007-05-26
:redface: :redface:#-o#-o
It helps if I use the right password.

---

### Post by K-a-M-u-Z-u on 2007-05-26
the command:
```
ssh -vv faqusrblk@82.144.223.155
```
gave:
> ssh -vv faqusrblk@82.144.223.155
OpenSSH_4.3p2 Debian-8ubuntu1, OpenSSL 0.9.8c 05 Sep 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 82.144.223.155 [82.144.223.155] port 22.
debug1: Connection established.
debug1: identity file /home/nir/.ssh/identity type -1
debug1: identity file /home/nir/.ssh/id_rsa type -1
debug1: identity file /home/nir/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-8ubuntu1
debug1: match: OpenSSH_4.3p2 Debian-8ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_init: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug2: mac_init: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 131/256
debug2: bits set: 511/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '82.144.223.155' is known and matches the RSA host key.
debug1: Found key in /home/nir/.ssh/known_hosts:1
debug2: bits set: 501/1024
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
debug2: key: /home/nir/.ssh/identity ((nil))
debug2: key: /home/nir/.ssh/id_rsa ((nil))
debug2: key: /home/nir/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/nir/.ssh/identity
debug1: Trying private key: /home/nir/.ssh/id_rsa
debug1: Trying private key: /home/nir/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug1: Next authentication method: password
faqusrblk@82.144.223.155's password: 
debug2: we sent a password packet, wait for reply
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.

and again, the password is correct,.no UPPERR-LOWER CASE MISTYPING, no language MISSTYPING, NO COPY PASTE...
thanks :)

---

### Post by tturrisi on 2007-05-26
fyi, gftp handles ssh connections very well.

---

### Post by K-a-M-u-Z-u on 2007-05-26
GFTP also says wrong password. :(

---

### Post by K-a-M-u-Z-u on 2007-05-28
Could it be something related to PUBLIC KEYS? i had in the first time i connect a messege about PUBLIC KEY and a YES\NO question.

---

### Post by PetePete on 2007-05-28
you could try cleaning your ~/.ssh/known_hosts file which contains the public keys.

---

### Post by K-a-M-u-Z-u on 2007-05-28
I have cleaned it, but when i connect again later i get:

> ssh faqusrblk@82.144.223.155The authenticity of host '82.144.223.155 (82.144.223.155)' can't be established.
RSA key fingerprint is 87:a2:54:ad:e7:b2:05:7c:09:49:98:c3:ee:4c:cb:b2.
Are you sure you want to continue connecting (yes/no)?
if i choose yes i get:
> Warning: Permanently added '82.144.223.155' (RSA) to the list of known hosts.
faqusrblk@82.144.223.155's password: 
Permission denied, please try again.

and again, the password is ok and i'm not mistyping or mispelling...

---

### Post by PetePete on 2007-05-28
urmmm untill someone posts a solution to this, you might want to try installing putty and seeing it you can connect with that

'sudo apt-get install putty'

ps... do you have a non-standard keyboard layout? (not US) might be something to do with that, although im clutching at straws here!

---

### Post by K-a-M-u-Z-u on 2007-05-28
i have two keyboard layouts.but i made sure that i'm using the US for the typing(and its the default...)

with putty i get "ACCESS DENIED"

---

### Post by tturrisi on 2007-05-28
If the message is "incorrect password" then know that somehow the password is incorrect!  The password could have been created using a different charset, numlocks pad for numbers, caps lock on accidentally.  Try recreating the sshd password on the remote server.  This can be done via webmin if it's installed on the bsd server.

---

### Post by K-a-M-u-Z-u on 2007-05-28
the password is 100% correct dude..
when i enter it in WINDOWS XP(i have dual boot here) i type the same password.
i did really slowly to make sure i type it correct...
under windows i used SSH SECURE HOST, PUTTY, CYGWIN and even APACHE CONF and the password was accepted...
only problem is only when i use UBUNTU...
any other ideas? maybe feisty has a but or something regarding SSH connection between UBUNTU to FreeBSD?

---

### Post by PetePete on 2007-05-28
open up a ssh connection so it asks you to enter your username (putty can easily do this)
when it prompts for the username, type your password.

This will check if the ssh client is using the correct keys and eliminate any possible errors from layouts/laptop function keys.

let me know if it displays correctly.

---

### Post by K-a-M-u-Z-u on 2007-05-28
well...i entered my pass as user name, but what about the password request later?
i tryed both user name and password...but both of them gave me wrong password...

i do use a laptop. IBM ThinkPad R40 2722-BDG.could this have something to do with that?
tnx

---

### Post by PetePete on 2007-05-29
I just said to enter your pass as the username so that you could see what characters was being inputted. 

Im all out of ideas, maybe someone else has some?!

---

### Post by mistermax on 2007-05-31
I get similar trying to sheel from Cygwin to my home box (Feisty)

$ ssh -vv [email]max@scunner.homelinux.org[/email]
OpenSSH_4.6p1, OpenSSL 0.9.8e 23 Feb 2007
debug2: ssh_connect: needpriv 0
debug1: Connecting to scunner.homelinux.org [87.112.64.28] port 22.
debug1: Connection established.
debug1: identity file /cygdrive/c/Documents and Settings/mrussell/.ssh/identity
type -1
debug1: identity file /cygdrive/c/Documents and Settings/mrussell/.ssh/id_rsa ty
pe -1
debug1: identity file /cygdrive/c/Documents and Settings/mrussell/.ssh/id_dsa ty
pe -1
debug1: Remote protocol version 2.0, remote software version dropbear_0.36
debug1: no match: dropbear_0.36
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.6
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-g
roup-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour1
28,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-c
tr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour1
28,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-c
tr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@open
ssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@open
ssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: kex_parse_kexinit: diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa
debug2: kex_parse_kexinit: 3des-cbc
debug2: kex_parse_kexinit: 3des-cbc
debug2: kex_parse_kexinit: hmac-sha1,hmac-md5
debug2: kex_parse_kexinit: hmac-sha1,hmac-md5
debug2: kex_parse_kexinit: none
debug2: kex_parse_kexinit: none
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: mac_init: found hmac-md5
debug1: kex: server->client 3des-cbc hmac-md5 none
debug2: mac_init: found hmac-md5
debug1: kex: client->server 3des-cbc hmac-md5 none
debug2: dh_gen_key: priv key bits set: 175/384
debug2: bits set: 496/1024
debug1: sending SSH2_MSG_KEXDH_INIT
debug1: expecting SSH2_MSG_KEXDH_REPLY
debug1: Host 'scunner.homelinux.org' is known and matches the RSA host key.
debug1: Found key in /cygdrive/c/Documents and Settings/mrussell/.ssh/known_host
s:5
debug2: bits set: 517/1024
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
debug2: key: /cygdrive/c/Documents and Settings/mrussell/.ssh/identity (0x0)
debug2: key: /cygdrive/c/Documents and Settings/mrussell/.ssh/id_rsa (0x0)
debug2: key: /cygdrive/c/Documents and Settings/mrussell/.ssh/id_dsa (0x0)
debug1: Authentications that can continue: password
debug1: Next authentication method: password
[email]max@scunner.homelinux.org[/email]'s password:
debug2: we sent a password packet, wait for reply
debug1: Authentications that can continue: password
Permission denied, please try again.


I've tried clearing out the ssh hosts...

---

