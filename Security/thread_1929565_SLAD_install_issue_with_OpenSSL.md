---
title: "SLAD install issue with OpenSSL"
date: 2012-02-22
forum: Security
---

### Post by shayno90 on 2012-02-22
I am attempting to install SLAD installer on Ubuntu 10.04 but have run into installation issues with setting up the RSA key and then try to load it into the SLAD installer as shown below:

Repository:
[http://wald.intevation.org/frs/?group_id=29](http://wald.intevation.org/frs/?group_id=29)

Download:
[http://wald.intevation.org/frs/download.php/516/sladinstaller-1.1.2.tar.gz](http://wald.intevation.org/frs/download.php/516/sladinstaller-1.1.2.tar.gz)

Install guide:
[http://www.openvas.org/using-slad.html](http://www.openvas.org/using-slad.html)

Installation:

user@user:~/sladinstaller-1.1.2$

[http://www.openvas.org/performing_lsc.html](http://www.openvas.org/performing_lsc.html)

Howto: Perform local security checks

This text explains how to run local security checks with OpenVAS. So far, this procedure has been tested only with Debian local security checks. 
Create users for local security checks

First, you need a key with certificate:

$ ssh-keygen -t rsa -f ~/.ssh/id_rsa_sshovas -C "OpenVAS-Local-Security-Checks-Key"
user@user:~$ ssh-keygen -t rsa -f ~/.ssh/id_rsa_sshovas -C "OpenVAS-Local-Security-Checks-Key"
Generating public/private rsa key pair.
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/user/.ssh/id_rsa_sshovas.
Your public key has been saved in /home/user/.ssh/id_rsa_sshovas.pub.
The key fingerprint is:
X:X:X:X:X:X:X:X:X:X:X:X:X:X:X:X:X OpenVAS-Local-Security-Checks-Key
The key's randomart image is:
X:X:X:X:X:X:X:X

**ISSUE 1:**
The key generation runs fine but verifying the key is the issue as it asks for an encryption password which I did not set and not sure what is:

user@user:~$ openssl pkcs8 -topk8 -v2 des3 -in ~/.ssh/id_rsa_sshovas -out sshovas_rsa.p8
Enter pass phrase for /home/user/.ssh/id_rsa_sshovas:
Enter Encryption Password:
Verifying - Enter Encryption Password:
Verification failure

a second attempt results with this error message:

user@user:~$ openssl pkcs8 -topk8 -v2 des3 -in ~/.ssh/id_rsa_sshovas -out sshovas_rsa.p8
Enter pass phrase for /home/user/.ssh/id_rsa_sshovas:
Enter Encryption Password:
Verifying - Enter Encryption Password:
unable to write 'random state'

How can this be corrected, are the appropriate flags been used?

Create user "sshovas":

user@user:~$ sudo su
root@user:/home/user# adduser --disabled-password sshovas
Adding user `sshovas' ...
root@user:/home/user# su - sshovas
sshovas@user:~$ mkdir .ssh
sshovas@user:~$ logout
root@user:/home/user# cp /home/user/.ssh/id_rsa_sshovas.pub /home/sshovas/.ssh/authorized_keys
When running the SLAD installer the following error message occurs:

root@user:/home/user# /usr/bin/sladinstaller 

**ISSUE 2:**
SLADINSTALLER window will appear, enter the following:

Package: [http://www.dn-systems.org/boss/slad-ng/dist/slad-2-current.tar.bz2](http://www.dn-systems.org/boss/slad-ng/dist/slad-2-current.tar.bz2)
Hostname: 127.0.0.1
Root password: XXXXXXXXXX
SLAD SSH Public Key:/home/user/.ssh/id_rsa_sshovas.pub

Error message:
Installation was not successfull. Could not login via SSH. If you don't have a public key installed be sure to set the following options in the sshd_config file:
PermitRootLogin yes
PasswordAuthentication yes

Apart from editing the sshd_config file how should the key verification process be corrected, plus is the correct keyfile being used and from the correct user?

---

### Post by shayno90 on 2012-02-23
**ISSUE 1 **
Is resolved by doing the following:

[http://stackoverflow.com/questions/94445/using-openssl-what-does-unable-to-write-random-state-mean](http://stackoverflow.com/questions/94445/using-openssl-what-does-unable-to-write-random-state-mean)

user@user:~$ sudo chown user:user ~/.rnd
user@user:~$ openssl pkcs8 -topk8 -v2 des3 -in ~/.ssh/id_rsa_sshovas -out sshovas_rsa.p8
Enter pass phrase for /home/user/.ssh/id_rsa_sshovas:
Enter Encryption Password:
Verifying - Enter Encryption Password:
user@user:~$ 

Working on issue 2 at the moment.

---

### Post by shayno90 on 2012-02-29
An update on the SLAD Installation, I have finally installed SLAD on the target machine however it was not a clean install.

Following my issue with the package not downloading on the target/remote  system, I tried changing the /etc/ssh(d)_config files and also  installing programs like corkscrew and connect-proxy in order to tunnel  SSH through HTTP proxy:

[http://en.kioskea.net/faq/2288-insta...rver-on-ubuntu]("http://en.kioskea.net/faq/2288-installing-a-ssh-server-on-ubuntu")

[http://www.ubuntugeek.com/how-to-use...in-ubuntu.html]("http://www.ubuntugeek.com/how-to-use-ssh-via-http-proxy-using-corkscrew-in-ubuntu.html")

This did not work (there is an option to set a proxy in the ssh_config file so best to use this instead)

Following theses attempts with HTTP proxy and adding more config files  to ./.ssh/ and checking permissions, the id_rsa file somehow got  corrupted by either moving it or the preceding changes. 
The error I got was :
debug1: Connection established.
debug1: identity file /home/user1/.ssh/identity type -1
debug3: Not a RSA1 key file /home/user1/.ssh/id_rsa.
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
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype

So the changes I made somehow corrupted the file but ssh still worked  via the terminal but not for the /usr/bin/sladinstaller on the local  system when ran. I debugged the local ssh server and got that error  message above so I moved the private id_rsa out of the .ssh directory.  This got rid of the error but the sladinstaller kept giving  authentication error messages as mentioned earlier in the thread. 

To avoid wasting more time troubleshooting I did this:

1. Remove all keys and files in .ssh directories on both local and remote machines (files like keys, known hosts etc)
2. Replace edited ssh_config and sshd_config files with unedited files of both
3. Generate new keys and verify the new keys
4. Copy new public key to remote .ssh directory
5. For Ubuntu users ensure, the user "root" account is enabled. Check  that all file permissions are as follows on local and remote hosts
chmod go-w ~/
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys
6. Check that ssh-server is installed on the target machine
[http://vibhorkumar.wordpress.com/201...ction-refused/]("http://vibhorkumar.wordpress.com/2011/04/13/ssh-connect-to-host-xxx-xx-xx-xxxx-port-22-connection-refused/")
7. Run the slad installer as normal user on the local machine and it  should run and download the package (although I am not sure why it can  now download the package from the server)
8. For Ubuntu users, disable the "root" account

Troubleshoot ssh connection issues such as bad permissions, corrupt keys with these links:

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)
[http://www.tek-tips.com/faqs.cfm?fid=6934](http://www.tek-tips.com/faqs.cfm?fid=6934)
[http://blog.codefront.net/2007/02/28...tion-problems/]("http://blog.codefront.net/2007/02/28/debugging-ssh-public-key-authentication-problems/")
[http://old.nabble.com/Bad-passphrase...d30553958.html]("http://old.nabble.com/Bad-passphrase-with-public-key-authentication-td30553958.html")
[http://www.noah.org/wiki/SSH_public_keys](http://www.noah.org/wiki/SSH_public_keys)
[https://help.ubuntu.com/community/SS...SH/Configuring]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring")

Time to test this simple installation!! (Hope this helps someone as the  instructions are minimal and non existent for certain stages of this  build)

---

