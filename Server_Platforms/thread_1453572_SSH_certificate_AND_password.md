---
title: "SSH certificate AND password"
date: 2010-04-13
forum: Server Platforms
---

### Post by van_Zeller on 2010-04-13
Hello,

I recently set up a simple home server that is also a media centre on my house. The server runs ubuntu 9.10. On my house I have a laptop also with ubuntu 9.10 and my flatmate has a macbook pro running osx leopard.

I changed the SSH configuration on the server to a certificate based authentication system, not because of security, but because I didn't want to be constantly typing in my password. 

eI was very pleased with this setup until I was at a friend's house and wanted to access the server. Of course this didn't work because she didn't have the certificate.

My question is: can you have a setup using certificates AND password authentication? So that if I log on from one of my computers, I use the certificate and if not, I use the password.

Thanks for any help

---

### Post by dannyboy79 on 2010-04-13
not sure what you mean a certificate. are you talking about an rsa or dsa key? just keep the key with you at all times. i'd have to ask you what the point would be if you had a fallback authentification of a pssword login if you didn't have the key? then everyone would still be trying to brute force your server. best way is to carry the id_rsa key with you or put it in the clouds. (dropbox or ubuntu one) so wherever you are, you'll be able to access the server.

---

### Post by Bachstelze on 2010-04-13
I assume that by "certificate" you mean SSH keys. Yes, it is perfectly possible to use both key-based and password-based authentication: just don't disable password-based auth, as you probably have.

---

### Post by van_Zeller on 2010-04-13
Hello

Thank you for the quick answers. 

Yes, by certificate I mean a pair of keys, public and private.

I am using a strong password...Also in this case I prefer to choose practicality over security, I guess.

When I try to log in as another user I get this:

```
ssh vanzeller@192.168.1.78
Permission denied (publickey).
```

Should I paste my sshd_config file? Or is it a security risk?

---

### Post by FuturePilot on 2010-04-13
> **van_Zeller said:**
> Hello

Thank you for the quick answers. 

Yes, by certificate I mean a pair of keys, public and private.

I am using a strong password...Also in this case I prefer to choose practicality over security, I guess.

When I try to log in as another user I get this:

```
ssh vanzeller@192.168.1.78
Permission denied (publickey).
```

Should I paste my sshd_config file? Or is it a security risk?

You have probably disabled password authentication. Make sure this is in your sshd_config
```
PasswordAuthentication yes
```
Yours probably says 'no'

---

### Post by van_Zeller on 2010-04-14
No, password authentication is set to allow. I figure my config can only help. Also, if you see anything obviously wrong please tell me. Thank you for all help.

```
# Package generated configuration file
# See the sshd(8) manpage for details

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
#AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

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

UsePAM yes
```

---

### Post by paulsp on 2010-04-14
Although this looks okay you can try commenting out the line about Password Authentication. 
```
#PasswordAuthentication yes
```Then restart SSH:
```
sudo /etc/init.d/ssh restart
```

---

### Post by van_Zeller on 2010-04-15
It is now working. I had to restart the daemon (duh!). Thanks for all help.

Thread marked as solved.

---

### Post by dannyboy79 on 2010-04-15
> **van_Zeller said:**
> It is now working. I had to restart the daemon (duh!). Thanks for all help.

Thread marked as solved.
my question to you would be why are you even using pubkey authentification if you're going to allow password attempted logins? just get rid of the pubkey's cause allowing pubkey login, you're still going to possible get brute forced. have fun with that.

---

### Post by van_Zeller on 2010-04-15
> **dannyboy79 said:**
> my question to you would be why are you even using pubkey authentification if you're going to allow password attempted logins? just get rid of the pubkey's cause allowing pubkey login, you're still going to possible get brute forced. have fun with that.

My password is made of more than 12 characters and no dictionary words. I took the time to estimate how long it would take a very good computer to crack my password and the result, according to:

[http://www.mandylionlabs.com/PRCCalc/BruteForceCalc.htm](http://www.mandylionlabs.com/PRCCalc/BruteForceCalc.htm)

Is  234,685,920,816.62 hours. I'll take my chances.

I keep the pubkey system in place because it allows faster logins without typing the pass every time.

---

### Post by dannyboy79 on 2010-04-16
to each his own........ does that take into account a botnet with over 1000 computers brute forcing you at once? or is that how long one computer would take trying to brute force you?

---

### Post by van_Zeller on 2010-04-17
To each his own, hear hear. I don't mean to sound cocky of obnoxious, I just mean I took a calculated risk where I weighed the risks and the benefits and made a choice. Keep in mind we're talking of a media centre here, not a CIA cluster.

As for your question, that was for a "very high performance" (from the excel file from the link I posted) machine. For a 1000 botnet - In all honesty I'm surprised you don't know the answer to your own question - just divide my previous number by 1000.

---

### Post by AntiBodies on 2011-04-17
(Almost a year to the day, sorry for resurrecting thread but all relevant stuff)

A SSH key (certificate whichever) is just like a super-complicated password that you happen to have written to a file in a sense. What really makes it secure is the fact it is tied to a user on the system and the username is unknown and shouldn't be hinted at in the key name etc. The key should also be used for a user-privileged user then once logged on a user would change there user to a sysadmin type user etc (root access). You should never be logging on as root via key or password authentication. As stated above, a key does protect a lot from ad-hoc network based brute force attempts.

Still especially if you are throwing that key around into the cloud and all over the place using a key is just as bad as a password if any malicious character or automated computer program wanted access to your super-secure PC all they need to do is make a quick copy of your key (a lot easier to make in the computing world than the physical). Yes, you can password encrypt your key but then that defeats the point of password-less login and then if someone copies that its even worse as then its un-detectable brute force attempts on your key.

SSH Key authentication is really for known places of remote access for example your house not the local internet cafe on a PC you dont trust. as in a place you know is secure you will leave your key there so it will have password-less access to your server. password authentication has an actual advantage in a random ad-hoc environment as the post user has found out. but ultimately both systems have flaws.

What I came to this forum to see is if you can configure SSH server (OpenSSH Daemon etc) to use a Password AND a certificate as in both are required for login (also not a password on the certificate). Has anyone seen any configurations on this.. I cant seem to find anything. This is common in a VPN type setup but doesn't seem to be common in SSH server setups.

---

### Post by dfreer on 2011-04-17
EDIT: Nevermind, didn't notice that you specified that it not be a password on the certificate itself.

---

### Post by van_Zeller on 2011-04-18
To the best of my knowledge, you can use Password authentication, pubkey authentication or either one. I've never heard of a system where you had tu use both.

Why would you want that, if you don't mind me asking?

---

### Post by usatonycuba on 2011-04-18
> **van_Zeller said:**
> To the best of my knowledge, you can use Password authentication, pubkey authentication or either one. I've never heard of a system where you had tu use both.

Why would you want that, if you don't mind me asking?

The reason is "strong and separated access privileges ", I think
> 
Open SSH is the most widely used SSH server on Linux. Using SSH, one can connect to a remote host and gain a shell access on it in a secure manner as all traffic is encrypted.
A neat feature of open SSH is to authenticate a user using a public/private key pair to log into the remote host. By doing so, you won't be prompted for the remote user's password.
Even though SSH is secured, there is tons of brute force attacks against SSH server which will attempt to gain access to your machine.
By using key based authentication and by disabling the standard user/password authentication, you will reduce the risk of having someone gaining access to your machine.

There is no a problem  when you use both, when you log in using pubkey authentication, you basically are the user sshd runs as.  So you can set up sshd without privilege separation so that way would be the  system account that is the one will use Pasword auth instead.

You can have both : 

pubkey authentication  <<< sshd user 
Password authentication  <<< system account user


IMHO

---

