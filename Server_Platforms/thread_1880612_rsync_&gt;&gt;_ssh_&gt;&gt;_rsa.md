---
title: "rsync &gt;&gt; ssh &gt;&gt; rsa"
date: 2011-11-14
forum: Server Platforms
---

### Post by DoubleD33D on 2011-11-14
So I'll explain the story. Me and my friend both host a local server(both Ubuntu 11.10 32bit). We have our ports forwarded all that works fine. Our FTP works fine. Our rsync works fine. Here the problem we have. We want to setup an hourly cron job to run out rsync command and sync out public folders. Well the rsync command works perfectly fine. Just gotta put it into crontab. Only thing is when we run our command it will as for the password of the remote host user password. We want this going both ways so we have a user on both servers, with the same home directory(/home/public) and same password for both users. So usera has to ssh to usera on the other server. But it asks for the password meaning we can't just put that into a cronjob. So what you want me to google before post stupid questions? Well we have read and done over and over and over about 50 differen't tutorials for stopping the password requirement in ssh sing rsa keys and no way will it NOT ask for the password. Everytime we tryed a different tutorial we made sure to rm -R .ssh so that we are sure to have a fresh start.

Here is a list of keywords to give you an idea of what we tryed
ssh-copy-id
cat
authentication_keys
authentication_keys2

Just no way will any user in any direction connect without asking for a password. We really need this to work.

---

### Post by markbl on 2011-11-14
You run "ssh-keygen" on your client pc and then "ssh-copy-id server". Enter a blank pass-phrase when you create the key with ssh-keygen.

---

### Post by spynappels on 2011-11-14
You may need to manually add the keys to the ~/.ssh/authorized_keys file for each user account. As long as the key is there, i.e. usera's key is in the ~/.ssh/authorized_keys file of the user as who you are running the ssh command, it should work.

---

### Post by SeijiSensei on 2011-11-14
Using shared keys is the best approach, but you might also want to look into running rsync in [daemon mode]("http://www.manpagez.com/man/1/rsync/") as an alternative solution.

---

### Post by papibe on 2011-11-14
I have the same approach to share data with my brother. As you mentioned, the key for unattended scripts is a passwordless connection. Here is a very useful [tutorial]("http://principialabs.com/beginning-ssh-on-ubuntu/") to set a system of public keys (check the Public-Key Authentication section).

You need to use an empty passphrase in order to do unattended script using rsync over ssh. Read carefully the security warnings, and may be increase the security of your network in other areas if necessary.

If you are going to share a few files, a simple rsync line will work. However, if:
[LIST=1]
[*]You are transfering lots of information.
[*]The time requiered to transfer the date is long.
[*]The connection is inestable.
[/LIST]
I would advice you to create a robust script. Take a look at my recommendations in this [thread]("http://ubuntuforums.org/showthread.php?t=1861143&highlight=rsync").

I hope that helps. Tell us how it goes.
Regards.

---

### Post by DoubleD33D on 2011-11-14
I have done all of this so far.

---

### Post by SeijiSensei on 2011-11-14
If you have shared keys configured correctly, you should be able to log into the server with ssh and not be prompted for a password.  Does that work?

---

### Post by DoubleD33D on 2011-11-14
Ok I've been able to get user a on host a to ssh to user a on host b without a password

now i want user a on host b to ssh to user a on host a without a password, but the steps hasnt seemed to work a second time around

---

### Post by DoubleD33D on 2011-11-14
We have messed with so much trying to get this its beyond repair. Should we reinstall the OS's and set it up again without error?

---

### Post by papibe on 2011-11-14
You can remove all keys by removing the proper directory on both ends:
```
rm -rf ~/.ssh
```
Then you can start from zero again.

Regards.

---

### Post by DoubleD33D on 2011-11-14
once again, done all of this things to try to make this work over and over and over and over again

---

### Post by familyguy.02 on 2011-11-14
I am the person who DoubleD33D is trying to get this set up with. We have been trying this for quite a while now to get SSH to connect without a password. The tutorials and manual files make sense and we follow them to the letter but it does not work. We are both running the same version of OpenSSH (OpenSSH_5.8p1 Debian-7ubuntu1, OpenSSL 1.0.0e 6 Sep 2011) and I think that there is a problem with a configuration files. Does anyone have some examples of working configuration files that they would like to share? (/etc/ssh/sshd_config, /etc/ssh/ssh_config) It would be greatly appreciated. Thanks!

---

### Post by spynappels on 2011-11-15
Ok, let's take this as two different tasks, but let me check that I have understood the requirements correctly (I'll use made-up names and hostnames):

paul on serverA wants to rsync to peter on serverB
peter on serverB wants to rsync on serverA

We'll do this in two steps, serverB to serverA first (I like doing things the wrong way round), then the other way around.

While logged into serverB as user peter, do the following:
```
ssh-keygen #(leave passphrase blank)
cd ~/.ssh
scp ./id_rsa.pub paul@serverA:/home/paul/
```

Then log into serverA as paul and do the following:
```
cat ~/id_rsa.pub >> ~/.ssh/authorized_keys
```

Also make sure that /etc/ssh/sshd_config has the following line in it on both servers
```
PubkeyAuthentication yes
```
Now you should be able to ssh to serverA as paul from serverB without being prompted for a password using ```
ssh paul@serverA
```

If this works, then repeat the procedure swapping serverA and serverB and peter and paul in the above steps.

Let us know if this worked.

---

### Post by markbl on 2011-11-15
Use "ssh -vvv server" to see what ssh is doing as it connects. Also check the sshd logs on the server in /var/log to see if it is complaining.

A *very* common problem people encounter with ssh is that they have the wrong permissions on their ~/.ssh dir and files on the server. In particular, make sure you have your home area not set group or world writable (otherwise somebody else in your group could move or replace your ~/.ssh dir and circumvent the key security). Usually your home area should be 755. All the files in ~/.ssh should be 600.

---

### Post by spynappels on 2011-11-15
> **markbl said:**
> 
A *very* common problem people encounter with ssh is that they have the wrong permissions on their ~/.ssh dir and files on the server. In particular, make sure you have your home area not set group or world writable (otherwise somebody else in your group could move or replace your ~/.ssh dir and circumvent the key security). Usually your home area should be 755. All the files in ~/.ssh should be 600.

Thanks Mark, forgot to mention that. You get an error message to that effect in any case. Good catch.

---

### Post by familyguy.02 on 2011-11-15
I followed your exact steps, chmodded the files to the exact specifications, but ultimately had no success. Here is what I got back from debugging:
```
drsync@HOSTNAME:~/.ssh$ ssh -vvv drsync@DOMAIN
OpenSSH_5.8p1 Debian-7ubuntu1, OpenSSL 1.0.0e 6 Sep 2011
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to DOMAIN [XX.XX.XX.XX] port 22.
debug1: Connection established.
debug1: could not open key file '/etc/ssh/ssh_host_key': No such file or directory
debug1: could not open key file '/etc/ssh/ssh_host_dsa_key': Permission denied
debug1: could not open key file '/etc/ssh/ssh_host_ecdsa_key': Permission denied
debug1: could not open key file '/etc/ssh/ssh_host_rsa_key': Permission denied
debug1: could not open key file '/etc/ssh/ssh_host_dsa_key': Permission denied
debug1: could not open key file '/etc/ssh/ssh_host_ecdsa_key': Permission denied
debug1: could not open key file '/etc/ssh/ssh_host_rsa_key': Permission denied
debug1: identity file /home/public/.ssh/id_rsa type -1
debug1: identity file /home/public/.ssh/id_rsa-cert type -1
debug1: identity file /home/public/.ssh/id_dsa type -1
debug1: identity file /home/public/.ssh/id_dsa-cert type -1
debug1: identity file /home/public/.ssh/id_ecdsa type -1
debug1: identity file /home/public/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.8p1 Debian-7ubuntu1
debug1: match: OpenSSH_5.8p1 Debian-7ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.8p1 Debian-7ubuntu1
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ssh-rsa-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-dss-cert-v00@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-rsa,ssh-dss
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
debug1: Server host key: ECDSA c1:9f:de:69:c1:4b:95:86:b2:c5:da:4a:eb:5f:a1:00
The authenticity of host 'DOMAIN (XX.XX.XX.XX)' can't be established.
ECDSA key fingerprint is c1:9f:de:69:c1:4b:95:86:b2:c5:da:4a:eb:5f:a1:00.
Are you sure you want to continue connecting (yes/no)? yes
Failed to add the host to the list of known hosts (/home/public/.ssh/known_hosts).
debug1: ssh_ecdsa_verify: signature correct
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
debug2: key: /home/public/.ssh/id_rsa ((nil))
debug2: key: /home/public/.ssh/id_dsa ((nil))
debug2: key: /home/public/.ssh/id_ecdsa ((nil))
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/public/.ssh/id_rsa
debug3: no such identity: /home/public/.ssh/id_rsa
debug1: Trying private key: /home/public/.ssh/id_dsa
debug3: no such identity: /home/public/.ssh/id_dsa
debug1: Trying private key: /home/public/.ssh/id_ecdsa
debug3: no such identity: /home/public/.ssh/id_ecdsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
drsync@DOMAIN's password:

```

I only censored out the domains and IPs of our systems for safety's sake. Looking at the debug info, it looks like our user just isn't allowed to access the files but I'll take you guys' expert opinions over my idiot mind.

---

### Post by DoubleD33D on 2011-11-15
Solved. Turns out the problem wasn't how we were copying the keys or the configurations file. The problem was the home folder ownership. We would create the users we want for rsync(users drsync) on both server, then we would make the home folders public, but we never chown to home folders to the users. That could also explain why we got it to work one way and not the other, one of us must have chowned the folder to the right user.

---

