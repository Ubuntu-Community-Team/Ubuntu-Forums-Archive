---
title: "proftpd over ssh"
date: 2007-11-11
forum: Server Platforms
---

### Post by thefunnyman on 2007-11-11
Ok, I am attempting to tunnel ftp via ssh ( putty ) on a windows machine to my ubuntu 7.10 desktop. I can connect to my domain remotely without using ssh just fine, but when I introduce ssh tunneling, my ftp client connects but no file listing is displayed. I am using Pspad's built in ftp client on my windows machine. I have 2 configurations in Pspad, one using my domain as the server, the other using localhost as my server. the one using my domain as the server works beautifully, but the one referencing localhost just does not create a file listing.

I have also experienced the same problem using [ftp://localhost](ftp://localhost) as opposed to [ftp://my.domain.net](ftp://my.domain.net) and the one referencing domain works, but not localhost. This makes me feel that there might be some type of proftpd configuration issue

proftpd.conf file:

```


# To really apply changes reload proftpd after modifications.
AllowForeignAddress on
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias userAlias userftp
MasqueradeAddress              domain.name.net
ServerName                      "ServerName"
ServerType                      standalone
DeferWelcome                    on

MultilineRFC2228 on
DefaultServer                   on
ShowSymlinks                    off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

TimeoutStalled 100
TimeoutIdle 2200

DisplayFirstChdir               .message
ListOptions                     "-l"

RequireValidShell               off

TimeoutLogin 20

RootLogin                       off

# It's better for debug to create log files ;-)
ExtendedLog                     /var/log/ftp.log
TransferLog                     /var/log/xferlog
SystemLog                       /var/log/syslog.log

#DenyFilter                     \*.*/

#DenyFilter                     \*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart               on

# Port 21 is the standard FTP port, so you may prefer to use another port for security reasons (choose here the port you wa$
# Port                          1980
Port                            21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                           022     022

PersistentPasswd                off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
# ServerIdent                  on       "you're at home"
ServerIdent off

# Set /home/FTP-shared directory as home directory
#DefaultRoot /home/FTP-shared
#DefaultRoot /var/www

# Lock all the users in home directory, ***** really important *****
DefaultRoot /var/www
DefaultRoot ~

MaxLoginAttempts    5


PassivePorts 60000 65535        # These ports should be safe...

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /var/www>
Umask 022 022
AllowOverwrite off
       <Limit All>
        AllowUser userftp
        Deny ALL
        </Limit>
</Directory>


#<IfModule mod_tls.c>
#   TLSEngine on
#   TLSLog /var/ftpd/tls.log
#   TLSProtocol TLSvl

#   TLSRequired off

#   TLSRSACertificateFile /etc/ftpcert/server.crt
#   TLSRSACertificateKeyFile /etc/ftpcert/server.key

#   TLSCACertificateFile /etc/ftpcert/ca.crt

#   TLSVerifyClient off
#</IfModule>


```

I followed the step by step in the following link to set up the ftp server:
[http://ubuntuforums.org/showthread.p...783#post429783](http://ubuntuforums.org/showthread.p...783#post429783)

I'm still pretty new to Ubuntu ( just a week running Windows-free ) and I'd like to be able to sit on my fat *** on the couch on my laptop and edit webpage files using Pspad. There are also instances where I cannot use ftp access ( protocol is blocked ) and that is my reasoning for using ssh tunneling. Can anyone give me any insight as to why ssh tunneling doesn't work?

Thanks in advance for any help. I would be more than happy to provide any additional config information for ssh/router/etc.

---

### Post by HermanAB on 2007-11-11
Uhmm, no.  SSH has a FTP service built in, called Secure Copy.  Use the scp command:
$ scp filename user@server:/wherever/.

Cheers,

Herman

---

### Post by thefunnyman on 2007-11-11
I don't understand.  Are you saying that it is impossible for me to tunnel ftp through ssh?  I thought I had read otherwise elsewhere, but I could be mistaken.  How exactly does the scp command work when I am ssh'd to my linux box from putty on my windows box?  I can pull files onto my windows machine with it and vice versa?

Thanks...

EDIT:  followed this link as well with no success.

[http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-SSH.html](http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-SSH.html)

---

### Post by HermanAB on 2007-11-11
You can use Filezilla on Windows to do SFTP graphically, or you can use PuTTY manually using scp:
$ man scp

Tunneling FTP over SSH is not easy - you have to use Passive mode.

Cheers,

H.

---

### Post by agent8131 on 2007-11-11
If your goal is just to be able to copy files securely than just running ssh on your ubuntu desktop and filezilla or winscp on the windows box is the easiest way to do that.  You can tunnel ftp traffic over ssh just like any other traffic but it heardly seems worth the effort unless you are trying to accomplish something besides file transfers.

---

### Post by thefunnyman on 2007-11-11
I don't understand why tunneling ftp through ssh is so difficult.  I've read every howto/tutorial I can find and still cannot seem to get it to work.  I don't want to use filezilla/winscp if I can use Pspad's built in ftp client to edit my web content.  I feel like using Pspad's ftp client is by far the easiest way to edit my web content remotely, assuming that I can get ftp through ssh tunnel working.  I'm not going to rule out pspad's inability to handle ftp via ssh ( in passive mode ) until I can get it to work in a web browser.   

I appreciate everyone's comments/suggestions thus far, but all I would like is a little more direction on tunneling ftp through ssh.  Are there modifications to my config file that I need to make, or are there additional steps that I need to take?

---

### Post by HermanAB on 2007-11-11
Two reasons why not to tunnel FTP over SSH:
a. SSH already has it built in, so there is not much point in it.
b. Standard FTP is quite complex. The initial negotiation is done over a fixed port, but the subsequent data transfer is done over a random high port (this reduces the server load and is essential for busy FTP servers). Therefore you need to configure the FTP server to use Passive Mode, which doesn't do that and uses only the fixed FTP port, otherwise, the connection will start and then the data transfer will fail - as  you seem to have found already.

Simply use PuTTY and copy the file using scp or use FileZilla and select SFTP as the protocol and use those to connect to the SSH Daemon on your Linux box.

Cheers,

Herman

---

### Post by thefunnyman on 2007-11-11
Again, thanks for your help.  I understand what you're trying to tell me.  That is still not what I am wanting to do.  I don't want to use Filezilla or scp.  I understand that you think that it is much more difficult and redundant to set this up the way I'm wanting.  I plan on being the only ftp user b/c this will ONLY be used for my personal remote web dev.  With that in mind, I am not concerned with ftp traffic or server load as far as ftp is concerned. 

Why could I not set PassivePorts in my proftpd.conf file to be something like 60000 60001 and forward those ports through my router and set them up in putty for tunneling?  

Based on what you said, if I could restrict passive ports to one or two ports and then set those up to tunnel, could/would that work?  I've tried and it does not seem to work.  Any thoughts?

---

### Post by HermanAB on 2007-11-11
Passive mode is probably the only way that you'll get it to work.  

However, FTP is built into sshd already.  See the bottom of /etc/ssh/sshd_config

# override default of no subsystems
Subsystem       sftp    /usr/lib/ssh/sftp-server

So, you are re-inventing the wheel, by adding another wooden wheel next to the existing steel belt radial...

Cheers,

H.

---

### Post by MJN on 2007-11-12
(I like the wheel analogy! :lol:)
 
SFTP (as built into SSH) is not the same as FTP over SSH. They are completely different protocols.
 
The OP has clearly stated they want to use a specific existing FTP client, yet wants the added security/privacy of encryption, so let's not try and force an alternative solution upon him (I'm SFTP's #1 fan but if the OP doesn't want to use it then they don't want to use it!).
 
To the OP, I've never used FTP over SSH myself so cannot guide you from experience, however I can say it is certainly doable and there a whole load of HowTo's out there telling you how so whilst the one you followed didn't work for your try another! Have you tried searching here at the forums?
 
Mathew

---

### Post by eldragon on 2007-11-12
putty even has psftp.exe , which works exactly like ftp.exe, but, under ssh.

if what you are looking is in graphical form, im sure a small google will help you out

---

### Post by thefunnyman on 2007-11-12
Thanks everyone for helping me out.  The ftp client I WAS attempting to use does not support sftp, that's why I was trying to tunnel ftp over ssh.  I've since found another editor to use that does support sftp, so I guess my problem has kind of been solved.  Still not the way I wanted to do it, but it works either way.

Thanks again.

---

### Post by cox377 on 2007-11-15
> **MJN said:**
> (I like the wheel analogy! :lol:)
 
SFTP (as built into SSH) is not the same as FTP over SSH. They are completely different protocols.
 
The OP has clearly stated they want to use a specific existing FTP client, yet wants the added security/privacy of encryption, so let's not try and force an alternative solution upon him (I'm SFTP's #1 fan but if the OP doesn't want to use it then they don't want to use it!).
 
To the OP, I've never used FTP over SSH myself so cannot guide you from experience, however I can say it is certainly doable and there a whole load of HowTo's out there telling you how so whilst the one you followed didn't work for your try another! Have you tried searching here at the forums?
 
Mathew

I'm wondering of another advantage of FTP over SSH,

I want to give someone secure read only access to a particular directory on the ubuntu server, however I don't want them to have shell access .

Any ideas how i can do this just using ssh-server or a simple work around?

---

