---
title: "How to access Ubuntu server from outside the network?"
date: 2014-03-20
forum: Server Platforms
---

### Post by Diana_Agostinho on 2014-03-20
Hello all, 

So I'm having a bit of trouble with my Ubuntu 12.04 LTS server that I created for my job. Basically the goal was to set up an internal server with a software RAID 1 setup that everyone on the local network could access with a login and password. Great! That works fine. However, when my boss wants to access his files from home, he can't. I have been trying to find the most secure way to set this up but I need to get this done ASAP so I have no time to try to figure all of this out on my own. Okay so here is my set up, I built this computer with an i3 intel processor, 16GB of ram, asus H87M motherboard, 3 1TB seagate HDD's, and those are the important parts. I wasn't able to update the firmware for the motherboard because it was only compatible with windows 7/8. I didn't want to clutter the setup so I did a clean install of Ubuntu server on the new disk and set everything up from there. So I have it connected via eth0 since I couldn't get wifi working from the drivers. Anyhow, I created a static IP and the server sits behind a router that I also reconfigured and set it to open a specific port that would route directly to the internal server. So now I am a bit stuck on where to go from here, what client to use to access the information from my MAC at home, and how to make this as simple as possible to connect to from outside the local network. My boss isn't tech savvy at all so ideally, I'd like to be able to set up a web page that he can log into with specific credentials and view the files in almost a windows explorer interface instead of a command-line interface. If there are reliable clients other than a browser interface to log in remotely, that would be fine too. Just need help on how to set this up! Oh and I already have OpenSSH and samba installed and configured on the server as well.

Let me know if you have any questions!

Thank you so much,

Diana Agostinho

---

### Post by volkswagner on 2014-03-20
I suggest using OpenVPN.

[https://help.ubuntu.com/12.04/serverguide/openvpn.html](https://help.ubuntu.com/12.04/serverguide/openvpn.html)

The clients can install openVPN for Windows, Mac users can Use TunnelBlick for the client. If you are the only mac, you can also simply use ssh.

You would only need the openVPN port like 1194 open and forwarded from router to the Server.

---

### Post by Diana_Agostinho on 2014-03-20
@volkswagner thanks so much for your reply! I'll give that a go and let you know how it works out!

---

### Post by d4m1r on 2014-03-24
OpenVPN is not needed and will most likely make things even more difficult. All he wants is to be able to remotely access files from the RAID drive?

A simple FTP server would handle that, with the ability to set a username/password of course. If you have opened a port in your router however (and restarted it right?) and it is STILL not accessible from the internet that is not good and there is something wrong with your router...

---

### Post by SeijiSensei on 2014-03-24
I suggest [WinSCP]("http://winscp.net/eng/index.php") for Windows clients.  It's akin to an FTP client that uses the "secure copy protocol" over SSH.  You'll need to punch a hole through the firewall so external machines can see the server's SSH port.  You might consider choosing an arbitrary high port (>1023) on your router and forward that back to port 22 on the server.  A bit of "security through obscurity" never hurts.

A web-based option might be [WebDAV]("http://www.webdav.org/").  Apache supports DAV via its [mod_dav]("http://httpd.apache.org/docs/2.2/mod/mod_dav.html") module. You'll want to use [SSL]("http://httpd.apache.org/docs/2.2/ssl/") to secure the connection.  The nice thing about DAV in Windows is that you can configure the remote folder to appear on the Windows desktop like any other directory.

I've not tried [owncloud]("http://owncloud.org/"), but it gets positive reviews from other posters here.  Maybe that is a solution for you.  It's in the repositories.

---

### Post by Jake_Barbieur on 2014-03-25
I second the FTP option.  I'd recommend checking out vsftp for use as an FTP server; it's very easy to install and configure.  As far as an FTP client is concerned, I like FileZilla, probably mostly because I'm familiar with it; there are probably plenty of other good FTP clients out there.  I like FileZilla for its simple interface and the fact that it's available for Linux, Windows, and OSX.  Alternatively, I believe you can just add an FTP site as a network location in Windows Explorer (assuming your boss is a Windows user).  This would probably be ideal since your boss is not so tech savvy.  

As far as you accessing the machine from a Mac, SSH is probably the way to go, although I sometimes find transferring files a little easier with an FTP client with a GUI.  If you do decide to install an FTP server, you should probably chroot your boss to their home directory so they don't cause any damage to the system.

---

### Post by robert-woodward on 2014-03-28
For what it's worth, I use sftp using openssh and the following settings:

/etc/ssh/sshd_config
```



# See the sshd_config(5) manpage for details


# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
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
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes


# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes


X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
TCPKeepAlive yes
#UseLogin no


#MaxStartups 10:30:60
#Banner /etc/issue.net


# Allow client to pass locale environment variables
AcceptEnv LANG LC_*


Subsystem sftp /usr/lib/openssh/sftp-server


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


Match GROUP sftp
  ChrootDirectory %h
  ForceCommand internal-sftp
  AllowTCPForwarding no


```

For this to work with the above settings you do have to do a few things

1.  Set up a group called "sftp" ```
groupadd sftp
```
2.  Add all users you want to be able to sftp in to the group ```
usermod -a -G sftp [COLOR=#000000]Diana[/COLOR]
```
3.  In the /home directory, the following file permissions:

from / (Root of drive, this should be as standard to be honest!)
```
drwxr-xr-x  11 root root  4096 Feb 28 18:57 home
```

then within /home
```
drwxr-xr-x  4 root  root        4096 Feb 28 17:26 [COLOR=#000000]Diana[/COLOR]
```

and then within /home/Diana
```
drwxrws--- 20 Diana Diana 4096 Mar 19 11:24 data
```

This will lock the users who remote in to their respective home drives.  You do have to do a bit more work if you have a shared folder in the home drive you want everyone to access doing this, whereby you mount the shared folder within each users area, i.e.:

```
mount -o bind /home/shared/data /home/Diana/data/shared
```

and to make it happen each time, add to the end of /etc/fstab for each user:
```

/home/shared/data /home/Diana/data/shared auto bind,gid=46,defaults 0 0

```


Hope this helps!

---

