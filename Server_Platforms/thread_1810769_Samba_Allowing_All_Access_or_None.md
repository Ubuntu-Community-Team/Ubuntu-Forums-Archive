---
title: "Samba Allowing All Access or None"
date: 2011-07-23
forum: Server Platforms
---

### Post by hateborne on 2011-07-23
First: Ubuntu Server 10.10 i386
 
I am trying to setup a file server to hold all my backup images. Basically I would like to be able to allow guest access to download/copy/"read" them ('myguest' user), set individuals to be able to add images (group: authuser), and allow myself full access.
 
I have spent the last several hours failing miserably. Any help would be greatly appreciated! I have spent so many hours following varying versions/operating-systems/etc that I can no longer tell which is correct and which is outdated syntax.
 
smb.conf
```

[global]
netbios name = MYSERVER
workgroup = WORKGROUP
server string = Samba %v on (%h)
security = share
guest account = myguest
map to guest = Bad Password
wins support = yes
encrypt passwords = yes
smb passwd file = /usr/bin/smbpasswd
interfaces = 127.0.0.1, 192.168.2.130/24
create mask = 0644
directory mask = 0755
 
[IMAGES]
comment = OPERATING SYSTEM IMAGES
path = /srv/samba/images
browsable = yes
read only = no
guest ok = yes
read list = myguest
write list = @authuser
admin users = @authuser

```
 
Permissions for the images folder
```

drwxrwsrwx 5 root authuser 4096 2011-07-23 16:25 images

```
 
Users in 'Authuser' // Passwords 
```

bob  //  bob123
todd  //  todd123

```
 
Thanks!

---

### Post by headvampyre@hotmail.co.uk on 2011-07-23
Does /usr/bin/smbpasswd even exist? For starters, i dont even think it should be in there, but in /etc/samba/smbpasswd. Also try running smbpasswd -a username

[http://www.samba.org/samba/docs/man/manpages-3/smbpasswd.8.html](http://www.samba.org/samba/docs/man/manpages-3/smbpasswd.8.html)

Use that for smbpasswd reference.

---

### Post by hateborne on 2011-07-23
Yes it does exist.
 
I linked it there because after TWO fresh installs of Ubuntu Server and Samba...it kept placing it there.
 
Also, both users were already created using smbpasswd. However, I am curious if creating the group must take place in smbpasswd (if such a thing is even possible).
 
-Hate

---

### Post by brighty22 on 2011-07-23
Plan what you want to achieve clearly, then do it in samba:

[LIST]
[*]Account with 'full access': hateborne
[*]Group for those who need write access: authuser
[*]Guests do not need a username, so it's simpler to leave 'myguest' out.
[/LIST]

Seeing as you need write access, add yourself to the authuser group. Therefore there are essentially 2 types of user who can get at the folder: those who can only read - guests, and those who can read and write - members of authuser.

```
sudo usermod -aG authuser hateborne
```

Add everyone you need to authuser in the same way as above, and create passwords for them with smbpasswd if required.

It's clear the group ownership of the folder will be 'authuser', and owner username may as well be yourself. Guests need to be able to read and execute (the latter to be able to get into the folder), therefore:

```
sudo chown -R hateborne:authuser /srv/samba/images
sudo chmod -R 775 /srv/samba/images
```

Then make a backup of your existing smb.conf:

```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.backup
```

And then change your original to something like this:

```
[global]
workgroup = WORKGROUP
netbios name = MYSERVER
server string = Samba %v on (%h)
dns proxy = no
log file = /var/log/samba/log.%m
max log size = 1000

security = user
encrypt passwords = true
passdb backend = tdbsam
obey pam restrictions = yes
map to guest = bad user

[IMAGES]
comment = OPERATING SYSTEM IMAGES
path = /srv/samba/images
browsable = yes
guest ok = yes
read only = no
create mask = 0775
directory mask = 0775
```

This should allow anyone, whether logged in or without an account (eg. viewing from Windows), to be able to read the images folder and copy etc., and anyone in the authuser group to be able to write to the share.

---

### Post by hateborne on 2011-07-26
You Sir/Ma'am, are amazing.
 
The Samba kicked right on and allowed the access I needed!
 
However...not 3 hours after I got this working and my router log was turning over (on a home router). I had 2 Chinese based IPs and one Spanish based IP port scanning using SMB and SSH. 
 
Now I've got a find a way to either secure the system from the outside (via used Cisco business router or DD-WRT modified home router) and/or move to another system of file transfer.
 
I am just trying to host a file storage with all the repair images I use, along with some miscellaneous tools I have built/bought. I am not needing something military grade but I do need something that will not be hacked daily.
 
brighty22, thank you again!
 
-Hate

---

### Post by doas777 on 2011-07-26
samba is not really appropriate for Internet-wide distribution, so i would recommend something more webish like authenticated ftp for large file downloads. ssh\scp will work as well. 

Do not forward SMB ports to the internet
```

Port 135/TCP - used by smbdPort 137/UDP - used by nmbdPort 138/UDP - used by nmbdPort 139/TCP - used by smbdPort 445/TCP - used by smbd
```

and make sure that your smb.conf "hosts Allow" is configured to allow only your internal subnet, and that UFW backs that up by restricting the ports above to your local lan.

---

### Post by brighty22 on 2011-07-26
Will you ever need/want to access the files from the internet? As doas recommends, lock samba ports down to local IP addresses only. It's a good rule to block all ports, and then allow individual ones on a case-by-case basis. 

As far as access from the internet, I wouldn't trust ftp even with /dev/null over the internet, so would suggest setting up OpenSSH, and creating a dedicated user for ssh who can only access that folder on the system.

---

### Post by hateborne on 2011-07-27
There is no telling when I would want to access it. Like I mentioned before, I will be using this to store restore images, software tools (both purchased and downloaded), and a family file storage.

The secondary purpose of this experiment was find a way that can securely support easy access through Windows clients. I am not hosting anything that requires military grade security, but I do not want it brought down daily. My father and siblings are constantly trying to keep digital copies of home movies, pictures, etc etc. Right now, they just have them on numerous DVDs and 2-3 external hard drives. If I can get a working file server that is somewhat easily accessible from the internet, I can cheaply and safely store terabytes of data. It would surely beat having to Linux LiveCD boot into failed/virus-loaded Windows computers to keep manually backing them up.

I was trying Samba because I can write a fairly minor VB script that would auto-connect, mount, and allow access without any real effort on the client end. I can navigate it all from command line with ease, however my siblings and father would be less inclined.

I guess OpenSSH and/or SFTP would be my next goal. 

Thank You!

-Hate

---

### Post by brighty22 on 2011-07-27
SSH is pretty much as good as it gets for simplicity, as well as security - especially if you tweak your settings and use key authentication etc. which Google can help with. It's possible to set up and lock down the entire service within all of 10 minutes.

If you can get your family to learn the basics of FileZilla or WinSCP, then online file storage over SFTP will be a breeze. Not sure about terabytes though - it would take years, at least on my connection :)

Backup, especially automatic, would be a bit more tricky. I know there are paid for Windows utilities (eg. [ExpanDrive]("http://www.expandrive.com/")) that can mount sftp connections so they appear as normal drives in explorer. Maybe your VB skills would come into use here. Or you could use windows's built in ftp capabilities, but tunnel the connection over SSH. There's also rsync...

---

### Post by hateborne on 2011-07-28
Heh no no, I didn't mean automatically backing up. Just a place where it can be safely stored permanently. Having to rebuild their laptops every 3-4 months is getting old. I also want my two 500gb externals to be usable again.

Brighty, thank you again for all the assistance.

-Hate

---

### Post by hateborne on 2011-08-01
Two final questions!

A) Is there anyway to allow multiple groups? 
Specifically, I am using this little bit at the end of my *sshd_config* to help prevent system overthrow. I also changed the 3 users in each group to appropriate share as their "home directory". (/srv/samba/images for *authuser*, /srv/samba/family for *authfamily*) Should I change the ChrootDirectory line to match, and if so how?
```

Match group authuser
ChrootDirectory /home/%u
X11Forwarding no
AllowTcpForwarding no
ForceCommand internal-sftp

```

B) Is there anyway to do a very simple chroot jail or lockdown to ONLY a few folders?
I have *authuser* and *authfamily* groups. The first only needs access to my system images, while the second will only need access to the family photos/movies/etc folder. 
Can I do:
```

## This uses a comma delimiter
Match group authuser, authfamily

```
```

## This uses the "Groups" keyword that appears in the man
Match Groups authuser authfamily

```
```

## This uses space delimiter (also mentioned in man)
Match group authuser authfamily

```

---

### Post by hateborne on 2011-08-02
Alright! It is finally finished and fully functional! The question I had was resolved through facerolling (trial and error).

Here are the final (slightly censored) files for future reference:

sshd_config
```

# What ports, IPs and protocols we listen for
Port X
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
PermitRootLogin no
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
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding no
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp internal-sftp

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

# Additional Info to Prevent Remote Login/Seizure
AllowGroups authfamily authuser
Match Group authfamily
        ChrootDirectory /srv/samba/
        AllowTcpForwarding no
        ForceCommand internal-sftp
Match Group authuser
        ChrootDirectory /srv/samba/
        AllowTcpForwarding no
        ForceCommand internal-sftp

```

smb.conf
```

[global]
workgroup = WORKGROUP
netbios name = MYSERVER
server string = Samba %v on (%h)
dns proxy = no
log file = /var/log/samba/log.%m
max log size = 1000
#hosts allow = 127.0.0.1 192.168.2.0/24
host deny = 0.0.0.0/0
security = user
encrypt passwords = true
passdb backend = tdbsam
obey pam restrictions = yes
map to guest = bad user

[IMAGES]
comment = OPERATING SYSTEM IMAGES
path = /srv/samba/images
browsable = yes
guest ok = no
read only = no
create mask = 0750
directory mask = 0750

[FAMILY]
comment = FAMILY PHOTOS AND VIDEOS
path /srv/samba/family
browsable = yes
guest ok = no
read only = no
create mask = 0750
directory mask = 0750

```

Basically, the biggest issue was I tried to use "/srv/samba/images" for *authuser* and "/srv/samba/family" for *authfamily*. This will not work due to permissions issue. I ended up changing to "/srv/samba" and this resolved it!

I ended up disallowing guests through permissions use (as I had 1 full compromise of the box in under 24h with improperly setup guest access). Using the 750 mask allowed the creator to obviously edit the files, the group members to read/execute it, and guests get nothing.

Thank you again to those that contributed.

---

