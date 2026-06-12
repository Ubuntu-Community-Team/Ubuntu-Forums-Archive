---
title: "[SOLVED] sshd_config not quite right"
date: 2008-12-29
forum: Security
---

### Post by Kissell on 2008-12-29
I am able to use ssh-keygen to create and use key pairs to login to other servers (like my web-host) after authorizing my public key on those servers...  However, I've been unable to configure sshd on one of my own Ubuntu boxes to allow me to use the keys I create.

I think I'm almost there, just missing something small...  When I attempt to connect via ssh to the Ubuntu server I configured, I can login with my password if I turn password authentication on in sshd_config, but I want to leave that off, I want it to use the keys I generated to login...  When I try that, it prompts me for the key's passphrase, but then says "read: Connection reset by peer".  I know it's verifying the passphrase, because if I type it in incorrectly it asks again...  so it seems to validate the passphrase then kill the connection.

Can anyone tell me what is wrong with my sshd_config?

I have no idea why this isn't working.

> 
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
ServerKeyBits 4096

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 7
PermitRootLogin no
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile      %h/.ssh/authorized_keys

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
PasswordAuthentication no

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

MaxStartups 10:30:60
Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes



---

### Post by Kissell on 2008-12-29
well, I put the public key in both my user $HOME/.ssh/authorized_keys and in /root/.ssh/authorized_keys and then I changed the /etc/init.d/sshd_config to "PermitRootLogin without-password"

This change allowed me to login using my RSA keys with the root user.

But I'd much rather use my normal user account and not root, and I'm completely stumped as to why that is not working.  

THIS DOES NOT WORK
> 
# ssh kissell@server -i id_rsa
server-kissell
Permission denied (publickey).


BUT THIS DOES WORK
> 
ssh root@server -i id_rsa


dubya T ef?

---

### Post by kevdog on 2008-12-29
Any further information when you try to login with the 

ssh -vvv ......

Those are 3 v's for very verbose output.

---

### Post by Kissell on 2008-12-29
I thought you were joking around...  but "-vvv" is a real option.

Anyway, the output wasn't much help, at least to me...  it just told me in more depth that it didn't work...  Basicaly, it's not getting "authentication succeeded" after I enter the passphrase with my user account.  I have the public key as authorized_keys in both (root and user) .ssh folders, and both are set with chmod 600 and only the respective user has access to the file... 

HERE IS FROM WHEN I CONNECT SUCCESSFULLY WITH ROOT ACCOUNT:
> 
Enter passphrase for key './id_rsa_kissell_at_server-kissell.pri': 
debug1: read PEM private key done: type RSA
debug3: sign_and_send_pubkey
debug2: we sent a publickey packet, wait for reply
debug1: Authentication succeeded (publickey).


HERE IS WHEN I TRY THE SAME KEY WITH MY USER ACCOUNT:
> 
Enter passphrase for key './id_rsa_kissell_at_server-kissell.pri': 
debug1: read PEM private key done: type RSA
debug3: sign_and_send_pubkey
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password


Note, that I turned password authentication back on in sshd_config so I could test easier...  It seems like this is going to be one of those little things I overlooked, but I've gone over this time and time again, for hours, and whatever it is I'm totally missing it.

---

### Post by Kissell on 2008-12-29
Does it matter that I created this key pair as the root account on the client?  is that why my other user can't use the key?

Everytime I try to run ssh-keygen as the normal user it looks like it runs, but it gives me empty files...  so I ran "sudo ssh-keygen" to create these keys...  But I don't think that should matter what user created them.

---

### Post by Kissell on 2008-12-29
I found my answer...  wow...  I have been fiddling with this for hours...  

I went into /etc/ssh/sshd_config and set StrictModes to No.  This fixed it so I could login with the regular user, as previously only using the root account was working.

> 
StrictModes
Specifies whether sshd(8) should check file modes and ownership of the user’s files and home directory before accepting login.  This is normally desirable because novices sometimes accidentally leave their directory or files world-writable.  The default is “yes”.


The reason I was having problems, is because I was trying to login from my laptop, which was set to dual-boot with windows, and I had moved my user home folder to a data partition that was shared with windows...  Linux can read and write to NTFS, but it can't use permissions, all files are used as full rights "chmod 777" when using a NTFS mounted drive and can't be altered.  

At the very beginning, I had suspected this may be a problem for ssh, and so I had moved my private key to a location on the ext3 partition and was trying to use it from there, with proper rights to the user...  however, STRICTMODES also checks to make sure that your home directory is not open to the world...  and my home directory was still set to the NTFS volume...  so really I had everything right, just strict_modes was on to help protect the private key... and I had a unique situation, as most users wouldn't have moved their home folder at all, and hardly anybody would put it on an NTFS parition... I just wanted my documents in the home folder to be accessible if I ever booted into windows to play games.

---

### Post by cariboo on 2008-12-29
Just FYI there are several programs that allow you to access an ext3 partiton from Windows. I personally use [Linux-Reader]("http://www.diskinternals.com/linux-reader/"), but there are several others available.

Jim

---

### Post by Kissell on 2008-12-29
yeah, i'm going to just do that...  

yay, yet another program to install manually in windows...

i didn't really have a problem doing it the way i was doing until...  although, everytime i logged into gnome it was complaining that I didn't have the proper rights set on the .dmrc file in my home folder...  which couldn't be set "properly" having the home folder on NTFS...  so this is definately strike two...  i'll probably just switch to use ext3.

actually, it's a really powerful machine, i may just see if the games I play will work in a virtual box, I never tried it, i've been dual booting just for gaming...  but if I can load them up just fine in a virtual box then I can abandon this sick need to dual boot at all.

---

